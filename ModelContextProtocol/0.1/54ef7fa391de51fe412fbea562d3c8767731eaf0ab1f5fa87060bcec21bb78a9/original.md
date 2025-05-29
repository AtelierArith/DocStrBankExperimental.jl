```
InitializeResult(; serverInfo::Dict{String,Any}, capabilities::Dict{String,Any},
               protocolVersion::String, instructions::String="") <: ResponseResult
```

Result returned in response to MCP protocol initialization.

# Fields

  * `serverInfo::Dict{String,Any}`: Information about the server implementation
  * `capabilities::Dict{String,Any}`: Server capabilities being reported
  * `protocolVersion::String`: Version of the MCP protocol being used
  * `instructions::String`: Optional usage instructions for clients
