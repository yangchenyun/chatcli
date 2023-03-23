# ChatCLI

ChatCLI is a command-line tool that uses the OpenAI GPT-3 API to provide a chat
bot interface that can answer your questions. It provides a simple and
intuitive way to interact with GPT-3 by asking questions and getting relevant
answers.

This command is in early development and the interface and log file format are
unstable and changing rapidly. I'd love to get feedback on what would make this
tool more useful.

## Installation

The following steps will guide you through the installation process:

1. Clone the repository with the following command:
```
git clone https://github.com/cthulahoops/chatcli.git
```

2. Navigate to the project directory:
```
cd chatcli
```

3. Install Poetry (if you haven't already) by following the official Poetry installation instructions: https://python-poetry.org/docs/#installation

These instructions will guide you through the process of installing Poetry on your machine. Once installed, you can easily manage dependencies and environments for your Python projects using Poetry.

4. Install ChatCLI using Poetry:

```
poetry shell
poetry install
```

5. Set your OpenAI API key in the environment variable `OPENAI_API_SECRET_KEY`.

6. Run chatcli

```
chatcli
```

Alternatively, you can install the dependencies using pip with:

```
pip install -r requirements.txt
```

## Usage

### Ask a question

To ask a question, just run chatcli:
```
chatcli
```
This will start a conversation with the chat bot, which will prompt you for a question. You can also include a text file as context for your question by using the `-f` or `--file` option:
```
chatcli --file myfile.txt
```

You can also specify the personality that the chat bot should use with the `-p` or `--personality` option:
```
chatcli --personality concise
```

### Continue a conversation

To continue a previous conversation, use the `chat` command with the `--continue` option:
```
chatcli --continue
```

### Show a conversation

To show a previous conversation, use the `show`:
```
chatcli show
```

### List all conversations

To list all the conversations that have been logged, use the `log` command:
```
chatcli log
```

### Tag a conversation

You can tag a conversation using the `tag` command:
```
chatcli tag mytag
```

### List all tags

To list all the tags that have been used, use the `tags` command:
```
chatcli tags
```

### Filter by tag

You can filter conversations by tag using the `-t` or `--tag` option:
```
chatcli log --tag mytag
```

### Remove a tag

You can remove a tag from a conversation using the `untag` command:
```
chatcli untag mytag
```

### Display usage

To display the number of tokens used and the token cost, use the `usage` command:
```
chatcli usage
```

## Examples

### Generate a README for this project

```
chatcli --quick --file chatcli.py --personality code
>> Generate a README.md for this project.
```

### Using ChatGPT to create commit messages

1. Make some changes to your code and stage them for commit:
```
git add -p
```

2. Use `git diff` to see the changes you've made and pipe them to ChatGPT's `chatcli.py` script to generate a commit message:
```
git diff --cached | chatcli -p commit
```

3. Make a commit with the generated message:
```
git commit -m "$(chatcli show)"
```

This will use the `show` command to display the last message generated by the chat bot, which is then used as the commit message.

That's it! You've successfully used ChatGPT to generate a commit message based on the changes you've made to your code.

## Contributing

If you wish to contribute to this project, please fork the repository and submit a pull request.
