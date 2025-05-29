```
ServerConfig(; name::String, version::String="1.0.0", 
           description::String="", capabilities::Vector{Capability}=Capability[],
           instructions::String="")
```

Define configuration settings for an MCP server instance.

# Fields

  * `name::String`: The server name shown to clients
  * `version::String`: Server version string
  * `description::String`: Human-readable server description
  * `capabilities::Vector{Capability}`: Protocol capabilities supported by the server
  * `instructions::String`: Usage instructions for clients
