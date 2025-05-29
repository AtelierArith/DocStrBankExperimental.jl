```
MCPLogger <: AbstractLogger
```

Define a custom logger for MCP server that formats messages according to protocol requirements.

# Fields

  * `stream::IO`: The output stream for log messages
  * `min_level::LogLevel`: Minimum logging level to display
  * `message_limits::Dict{Any,Int}`: Message limit settings for rate limiting
