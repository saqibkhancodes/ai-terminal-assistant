# ask - AI Terminal Assistant

A simple command-line tool that turns English into Linux and macOS terminal commands using the Gemini API.

I built this because I was tired of dealing with Ubuntu's PEP 668 (`externally-managed-environment`) errors and bloated Python SDKs. This script uses zero external dependencies—it just makes a raw HTTP POST request using Python's built-in `urllib` to get the job done. 

## Why use this?
* **No pip installs needed:** Bypasses virtual environments and package manager conflicts entirely.
* **No markdown BS:** It is prompted to return *only* the raw, executable command. No chatty text, no backticks.
* **Global command:** Runs natively as `ask` from any directory in your terminal.

## Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/saqibkhancodes/ai-terminal-assistant.git 
   cd ai-terminal-assistant
   ```

2. Make it a global command:
   ```bash
   chmod +x ask
   sudo mv ask /usr/local/bin/
   ```

3. Add your Gemini API key as an environment variable:
   
   **For Linux (Ubuntu/Debian):**
   ```bash
   echo 'export GEMINI_API_KEY="your_api_key_here"' >> ~/.bashrc
   source ~/.bashrc
   ```

   **For macOS (Zsh):**
   ```bash
   echo 'export GEMINI_API_KEY="your_api_key_here"' >> ~/.zshrc
   source ~/.zshrc
   ```

## Usage

Just type `ask` followed by what you want the terminal to do:

```bash
$ ask "find all empty directories in my documents and delete them"

💡 Suggested Command:
find ~/Documents -type d -empty -delete
```

```bash
$ ask "show me the top 5 RAM heavy processes"

💡 Suggested Command:
ps aux --sort=-%mem | head -n 6
```
