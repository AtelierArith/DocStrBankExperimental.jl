```
Server(config::ServerConfig)
```

Represent a running MCP server instance that manages resources, tools, and prompts.

# Fields

  * `config::ServerConfig`: Server configuration settings
  * `resources::Vector{Resource}`: Available resources
  * `tools::Vector{Tool}`: Available tools
  * `prompts::Vector{MCPPrompt}`: Available prompts
  * `resource_templates::Vector{ResourceTemplate}`: Available resource templates
  * `subscriptions::DefaultDict{String,Vector{Subscription}}`: Resource subscription registry
  * `progress_trackers::Dict{Union{String,Int},Progress}`: Progress tracking for operations
  * `active::Bool`: Whether the server is currently active

# Constructor

  * `Server(config::ServerConfig)`: Creates a new server with the specified configuration
