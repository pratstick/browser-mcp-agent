# Browser MCP Agent

## Overview

The Browser MCP Agent is an enterprise-grade web automation solution that integrates OpenAI's GPT-4.1 Mini language model with browser automation capabilities through Anthropic's Model Context Protocol (MCP) and the Puppeteer automation framework. This system provides a natural language interface for programmatic web interaction and data extraction operations.

## Core Capabilities

The system provides the following functionality:

- **Natural Language Processing Interface**: Processes user commands in natural language to execute browser automation tasks
- **Automated Web Interaction**: Performs programmatic navigation, element interaction, and form submission operations
- **Visual Content Capture**: Generates screenshots and visual documentation of web page states
- **Complex Workflow Execution**: Orchestrates multi-step browsing sequences through a single command interface
- **Real-time Monitoring**: Provides live feedback and status updates through the Streamlit-based user interface
- **Protocol-based Integration**: Utilizes the Model Context Protocol for standardized communication between language models and automation tools

## Technical Specifications

### System Components

- **Language Model**: OpenAI GPT-4.1 Mini (Model Version: 2025-04-14)
- **Browser Automation Engine**: Puppeteer via Model Context Protocol Server
- **Communication Protocol**: Anthropic Model Context Protocol (MCP)
- **User Interface**: Streamlit Web Application Framework
- **Runtime Environment**: Python with Asynchronous I/O (asyncio)
- **Agent Framework**: mcp-agent library


### System Requirements

- Python Runtime Environment 3.8 or higher
- Node.js Runtime Environment with npm package manager
- Valid OpenAI API credentials

## Installation and Configuration

### Step 1: Repository Setup

```bash
git clone <repository-url>
cd MCP-Web_search
```

### Step 2: Dependency Installation

Execute the following command to install required Python packages:

```bash
pip install -r requirements.txt
```

### Step 3: API Key Configuration

Configure your OpenAI API credentials using one of the following methods:

**Method A: Environment Variable**
```bash
export OPENAI_API_KEY="your-api-key-here"
```

**Method B: Environment File**
Create a `.env` file in the project root directory:
```
OPENAI_API_KEY=your-api-key-here
```

### Step 4: Runtime Verification

Verify that Node.js is properly installed for Puppeteer MCP server functionality:

```bash
node --version
npm --version
```

## Operation and Usage

### Application Startup

To initialize the Browser MCP Agent system, execute the following command:

```bash
streamlit run main.py
```

The application will be accessible via web browser at the following address: `http://localhost:8501`

### Command Interface

The system accepts natural language commands for browser automation tasks. The following examples demonstrate supported command patterns:

#### Basic Navigation Commands
- `"Navigate to wikipedia.org/wiki/computer_vision"`
- `"Access google.com and perform a search for 'machine learning'"`

#### Interactive Element Commands
- `"Click the first available link and capture a screenshot"`
- `"Scroll down on the current page and generate a content summary"`
- `"Populate the search form with the term 'artificial intelligence'"`

#### Complex Workflow Commands
- `"Navigate to Wikipedia, search for 'neural networks', and provide a summary of the primary article"`
- `"Access a news website, locate the featured story, and extract key information"`
- `"Visit an e-commerce platform, search for laptop products, and analyze the top three results"`

## System Configuration

### Configuration File Structure

The system configuration is managed through the `mcp_agent.config.yaml` file with the following specification:

```yaml
execution_engine: asyncio
logger:
  transports: [console, file]
  level: debug
  progress_display: true
  path_settings:
    path_pattern: "logs/mcp=agent-{unique_id}.jsonl"
    unique_id: "timestamp"
    timestamp_format: "%Y%m%d_%H%M%S"

mcp:
  servers:
    puppeteer:
      command: "npx"
      args: ["-y", "@modelcontextprotocol/server-puppeteer"]

openai:
  default_model: "gpt-4.1-mini-2025-04-14"
```

### Configuration Parameters

- **Model Configuration**: Specifies GPT-4.1 Mini as the default language model
- **MCP Server Configuration**: Defines Puppeteer server parameters for browser automation
- **Logging Configuration**: Establishes debug-level logging with both console and file output
- **Execution Engine**: Configures asyncio for asynchronous operation handling

## System Architecture

The Browser MCP Agent implements a layered architecture as illustrated below:

```
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│   Streamlit UI  │────│  MCP Agent   │────│   OpenAI LLM    │
└─────────────────┘    └──────────────┘    └─────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  MCP Protocol    │
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │ Puppeteer Server │
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │   Web Browser    │
                    └──────────────────┘
```

## Project Structure

```
MCP-Web_search/
├── main.py                    # Application entry point and Streamlit interface
├── mcp_agent.config.yaml      # System configuration file
├── requirements.txt           # Python dependency specifications
├── logs/                      # System log directory (automatically generated)
└── README.md                  # Documentation file
```

## Functional Capabilities

The Browser MCP Agent provides the following operational capabilities:

### Navigation Operations
- URL navigation and page traversal
- Hyperlink following and browser history management
- Multi-directional navigation (forward/backward)

### Element Interaction
- Interactive element activation (buttons, links, controls)
- Form field population and data entry
- Dropdown menu selection and form submission

### Content Processing
- Text extraction and data analysis
- Page structure analysis and content parsing
- Information retrieval and data mining

### Visual Documentation
- Full-page screenshot capture
- Element-specific visual capture
- Visual state documentation

### Page Management
- Viewport manipulation (scrolling, zooming, resizing)
- Multi-tab session management
- Browser window control and coordination

## Logging and Monitoring

### Log Generation

The system automatically generates comprehensive logs in the `logs/` directory containing:

- Agent initialization and configuration data
- Tool availability and utilization metrics
- Language model interaction records
- Browser automation action logs
- Error tracking and diagnostic information

### Log File Naming Convention

Log files follow the standardized pattern: `mcp=agent-{timestamp}.jsonl`

Where `{timestamp}` follows the format specified in the configuration file (`%Y%m%d_%H%M%S`).

## System Limitations

### Technical Constraints

- **Network Dependency**: Requires stable internet connectivity for optimal operation
- **Website Compatibility**: Certain websites may implement automated access prevention measures
- **API Rate Limiting**: OpenAI API usage limits may affect system throughput
- **JavaScript Compatibility**: Single Page Applications (SPAs) with heavy JavaScript may require additional processing time
- **Security Restrictions**: CAPTCHA systems and advanced bot detection mechanisms may prevent access

## Security and Compliance

### Security Best Practices

- **Credential Management**: OpenAI API keys must be stored securely and excluded from version control systems
- **Legal Compliance**: Users must adhere to website Terms of Service when implementing automated interactions
- **Rate Limiting**: Production deployments should implement appropriate rate limiting mechanisms
- **Data Handling**: All extracted web data should be reviewed and sanitized before use

## Development and Contribution

### Contribution Guidelines

1. Fork the repository to your GitHub account
2. Create a feature branch using the naming convention: `feature/descriptive-feature-name`
3. Implement changes with appropriate documentation and testing
4. Commit changes with descriptive commit messages
5. Submit a Pull Request with detailed description of modifications

## License

This project is distributed under the MIT License. Please refer to the LICENSE file for complete terms and conditions.

## Dependencies and Acknowledgments

### Core Dependencies

- **Anthropic Model Context Protocol**: Protocol framework for standardized LLM-tool communication
- **OpenAI GPT-4.1 Mini**: Language model for natural language processing and command interpretation
- **Puppeteer**: Browser automation library for programmatic web interaction
- **Streamlit**: Web application framework for user interface development
- **mcp-agent**: Agent framework for Model Context Protocol integration
