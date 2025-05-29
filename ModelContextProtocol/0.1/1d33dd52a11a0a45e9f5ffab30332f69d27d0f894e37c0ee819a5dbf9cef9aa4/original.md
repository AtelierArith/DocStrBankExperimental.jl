```
InitializeParams(; capabilities::ClientCapabilities=ClientCapabilities(),
               clientInfo::Implementation=Implementation(),
               protocolVersion::String) <: RequestParams
```

Parameters for MCP protocol initialization requests.

# Fields

  * `capabilities::ClientCapabilities`: Client capabilities being reported
  * `clientInfo::Implementation`: Information about the client implementation
  * `protocolVersion::String`: Version of the MCP protocol being used
