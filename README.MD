# Claude Language Model Course

A comprehensive course on working with Anthropic's Claude language model, covering API integration, prompt engineering, tool development, and advanced techniques for building AI-powered applications.

## 📚 Course Overview

This course teaches you how to effectively work with Claude's API, from basic requests to advanced features like tool integration, RAG (Retrieval Augmented Generation), and agent development. You'll learn practical techniques for building production-ready AI applications.

## 🎯 Learning Objectives

By the end of this course, you'll be able to:

- Make API requests to Claude models (Opus, Sonnet, Haiku)
- Implement multi-turn conversations with context management
- Use system prompts to customize Claude's behavior
- Control model output with temperature and other parameters
- Implement response streaming for better user experience
- Build and integrate custom tools with Claude
- Create structured data extraction pipelines
- Implement RAG systems for document processing
- Develop evaluation frameworks for prompt optimization
- Build agents and workflows for complex tasks
- Use MCP (Model Context Protocol) for tool integration
- Implement Claude Code and Computer Use capabilities

## 🏗️ Course Structure

### Module 1: Claude Model Fundamentals

- **Model Families**: Understanding Opus, Sonnet, and Haiku
- **API Access Flow**: 5-step process from user input to response
- **Making Requests**: Basic API integration and message structure
- **Multi-Turn Conversations**: Context management and conversation history

### Module 2: Prompt Engineering

- **System Prompts**: Customizing Claude's behavior and role
- **Temperature Control**: Managing randomness in responses
- **Response Streaming**: Real-time response delivery
- **Output Control**: Pre-filling and stop sequences
- **Structured Data**: Clean data extraction techniques

### Module 3: Prompt Evaluation

- **Evaluation Workflows**: Systematic prompt testing
- **Test Dataset Generation**: Creating comprehensive test cases
- **Model-Based Grading**: Automated response evaluation
- **Code-Based Grading**: Syntax and validation testing

### Module 4: Advanced Prompting Techniques

- **Being Clear and Direct**: Action-oriented prompt writing
- **Being Specific**: Adding guidelines and steps
- **XML Tags**: Structured content organization
- **Examples**: One-shot and multi-shot prompting

### Module 5: Tool Integration

- **Tool Functions**: Building custom Python tools
- **Tool Schemas**: JSON schema specifications
- **Message Blocks**: Handling multi-block responses
- **Tool Results**: Managing tool execution and responses
- **Multi-Turn Tool Conversations**: Complex tool workflows

### Module 6: Advanced Tool Features

- **Batch Tools**: Parallel tool execution
- **Structured Data Tools**: Alternative to prompt-based extraction
- **Fine-Grained Tool Calling**: Streaming with tools
- **Built-in Tools**: Text Editor and Web Search capabilities

### Module 7: RAG (Retrieval Augmented Generation)

- **Text Chunking Strategies**: Size-based, structure-based, semantic
- **Text Embeddings**: Numerical text representations
- **Vector Search**: Similarity-based retrieval
- **Hybrid Search**: Combining semantic and lexical search
- **Reranking**: LLM-based result optimization
- **Contextual Retrieval**: Adding context to chunks

### Module 8: Advanced Claude Features

- **Extended Thinking**: Reasoning time for complex tasks
- **Image Support**: Processing and analyzing images
- **PDF Support**: Document processing capabilities
- **Citations**: Source attribution and verification
- **Prompt Caching**: Performance optimization

### Module 9: MCP (Model Context Protocol)

- **MCP Architecture**: Client-server communication
- **Server Implementation**: Creating MCP servers
- **Client Integration**: Connecting to MCP servers
- **Resources**: Data exposure mechanisms
- **Prompts**: Pre-defined prompt templates

### Module 10: Claude Code and Computer Use

- **Claude Code Setup**: Terminal-based coding assistant
- **MCP Server Integration**: Extending Claude Code capabilities
- **Parallelization**: Multiple Claude instances
- **Computer Use**: Visual interface interaction
- **Automated Debugging**: Production error handling

### Module 11: Agents and Workflows

- **Workflow Patterns**: Evaluator-optimizer, parallelization, chaining, routing
- **Agent Design**: Tool abstraction and environment inspection
- **Workflows vs Agents**: When to use each approach
- **Best Practices**: Reliability and user experience considerations

## 🛠️ Technical Requirements

### Prerequisites

- Python 3.8+
- Basic understanding of APIs and HTTP requests
- Familiarity with JSON and Python dictionaries
- Knowledge of basic programming concepts

### Required Packages

```bash
pip install anthropic python-dotenv
```

### Optional Packages (for advanced features)

```bash
pip install voyageai  # For embeddings
pip install pydantic  # For MCP development
pip install mcp      # For MCP server/client
```

## 🚀 Getting Started

### 1. Environment Setup

```bash
# Clone the repository
git clone <repository-url>
cd genAiAnthropic

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env and add your Anthropic API key
```

### 2. API Key Configuration

Create a `.env` file in your project root:

```
ANTHROPIC_API_KEY=your_api_key_here
```

### 3. Basic Usage Example

```python
import anthropic
import os
from dotenv import load_dotenv

load_dotenv()

client = anthropic.Anthropic(api_key=os.getenv("ANTHROPIC_API_KEY"))

response = client.messages.create(
    model="claude-3-sonnet-20240229",
    max_tokens=1000,
    messages=[{"role": "user", "content": "Hello, Claude!"}]
)

print(response.content[0].text)
```

## 📁 Project Structure

```
genAiAnthropic/
├── README.MD                 # This file
├── 001_requests.ipynb       # Basic API requests
├── 002_requests_input.ipynb # Input handling examples
├── requirements.txt         # Python dependencies
├── .env                     # Environment variables (not in git)
└── examples/               # Code examples by module
    ├── basic_requests/
    ├── prompt_engineering/
    ├── tool_integration/
    ├── rag_systems/
    └── agents_workflows/
```

## 🎓 Key Concepts

### Claude Model Selection

- **Opus**: Highest intelligence, complex reasoning, higher cost
- **Sonnet**: Balanced intelligence, speed, and cost (recommended)
- **Haiku**: Fastest, cost-efficient, no reasoning capabilities

### Prompt Engineering Principles

1. **Be Clear and Direct**: Start with action verbs
2. **Be Specific**: Add guidelines and steps
3. **Use Structure**: XML tags for content organization
4. **Provide Examples**: One-shot and multi-shot prompting
5. **Evaluate Systematically**: Use evaluation frameworks

### Tool Development Best Practices

1. **Descriptive Names**: Clear function and argument names
2. **Input Validation**: Validate inputs and provide meaningful errors
3. **Error Handling**: Graceful error handling with retry capabilities
4. **Schema Documentation**: Comprehensive JSON schemas

### RAG Implementation Guidelines

1. **Chunking Strategy**: Choose based on document structure
2. **Hybrid Search**: Combine semantic and lexical search
3. **Reranking**: Use LLM for result optimization
4. **Context Addition**: Add contextual information to chunks

## 🔧 Advanced Features

### Streaming Responses

```python
response = client.messages.create(
    model="claude-3-sonnet-20240229",
    max_tokens=1000,
    messages=[{"role": "user", "content": "Tell me a story"}],
    stream=True
)

for chunk in response:
    if chunk.type == "content_block_delta":
        print(chunk.delta.text, end="")
```

### Tool Integration

```python
def get_current_datetime(date_format="%Y-%m-%d %H:%M:%S"):
    return datetime.now().strftime(date_format)

tool_schema = {
    "name": "get_current_datetime",
    "description": "Get the current date and time",
    "input_schema": {
        "type": "object",
        "properties": {
            "date_format": {"type": "string", "description": "Date format string"}
        }
    }
}
```

### MCP Server Example

```python
import mcp
from pydantic import Field

@mcp.tool(name="read_document", description="Read document contents")
def read_document(doc_id: str = Field(description="Document ID")):
    # Implementation here
    return {"content": "Document content"}
```

## 📊 Evaluation and Testing

### Prompt Evaluation Framework

1. **Create Test Dataset**: Generate comprehensive test cases
2. **Run Evaluations**: Test prompts against dataset
3. **Grade Responses**: Use model-based or code-based grading
4. **Iterate**: Improve prompts based on scores

### Example Evaluation

```python
def evaluate_prompt(prompt, test_cases):
    scores = []
    for case in test_cases:
        response = run_prompt(prompt, case)
        score = grade_response(response, case)
        scores.append(score)
    return sum(scores) / len(scores)
```

## 🚀 Production Considerations

### Performance Optimization

- **Prompt Caching**: Reuse computational work
- **Streaming**: Real-time response delivery
- **Concurrent Processing**: Parallel request handling
- **Rate Limiting**: Respect API limits

### Security Best Practices

- **API Key Management**: Secure storage and rotation
- **Input Validation**: Sanitize user inputs
- **Error Handling**: Graceful failure modes
- **Access Control**: Implement proper authorization

### Monitoring and Logging

- **Request Logging**: Track API usage and performance
- **Error Monitoring**: Capture and analyze failures
- **Cost Tracking**: Monitor token usage and costs
- **Quality Metrics**: Track response quality over time

## 🤝 Contributing

This course is designed for learning and experimentation. Feel free to:

1. Fork the repository
2. Create feature branches
3. Submit pull requests
4. Report issues and bugs
5. Suggest improvements

## 📚 Additional Resources

### Official Documentation

- [Anthropic API Documentation](https://docs.anthropic.com/)
- [Claude Model Overview](https://www.anthropic.com/models)
- [MCP Documentation](https://modelcontextprotocol.io/)

### Community Resources

- [Anthropic Community](https://community.anthropic.com/)
- [GitHub Discussions](https://github.com/anthropics/anthropic-sdk-python/discussions)
- [Discord Server](https://discord.gg/anthropic)

### Related Courses and Tutorials

- Prompt Engineering Fundamentals
- LLM Application Development
- Vector Databases and Embeddings
- AI Agent Development

## 📄 License

This course material is provided for educational purposes. Please refer to Anthropic's terms of service for API usage guidelines.

## 🙏 Acknowledgments

- Anthropic team for creating Claude and providing excellent documentation
- The open-source community for tools and libraries
- Course participants for feedback and contributions

---

**Happy Learning! 🚀**

Start with the basic requests notebook and work your way through the modules. Each builds upon the previous, so take your time to understand the concepts before moving forward.
