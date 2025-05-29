```
mcp_server(; name::String, version::String="2024-11-05", 
         tools::Union{Vector{MCPTool},MCPTool,Nothing}=nothing,
         resources::Union{Vector{MCPResource},MCPResource,Nothing}=nothing, 
         prompts::Union{Vector{MCPPrompt},MCPPrompt,Nothing}=nothing,
         description::String="", 
         capabilities::Vector{Capability}=default_capabilities(),
         auto_register_dir::Union{String,Nothing}=nothing) -> Server
```

Primary entry point for creating and configuring a Model Context Protocol (MCP) server.

# Arguments

  * `name::String`: Unique identifier for the server instance
  * `version::String`: Server implementation version
  * `tools`: Tools to expose to the model
  * `resources`: Resources available to the model
  * `prompts`: Predefined prompts for the model
  * `description::String`: Optional server description
  * `capabilities::Vector{Capability}`: Server capability configuration
  * `auto_register_dir`: Directory to auto-register components from

# Returns

  * `Server`: A configured server instance ready to handle MCP client connections

# Example

```julia
server = mcp_server(
    name = "my-server",
    description = "Demo server with time tool",
    tools = MCPTool(
        name = "get_time",
        description = "Get current time",
        parameters = [],
        handler = args -> Dates.format(now(), "HH:MM:SS")
    )
)
start!(server)
```
