```
register!(server::Server, component::Union{Tool,Resource,MCPPrompt}) -> Server
```

Register a tool, resource, or prompt with the MCP server.

# Arguments

  * `server::Server`: The server to register the component with
  * `component`: The component to register (can be a tool, resource, or prompt)

# Returns

  * `Server`: The server instance for method chaining
