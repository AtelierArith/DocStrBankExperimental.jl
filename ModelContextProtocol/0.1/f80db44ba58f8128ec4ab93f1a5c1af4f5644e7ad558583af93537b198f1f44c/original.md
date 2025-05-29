```
RequestContext(; server::Server, request_id::Union{RequestId,Nothing}=nothing, 
             progress_token::Union{ProgressToken,Nothing}=nothing)
```

Store the current request context for MCP protocol handlers.

# Fields

  * `server::Server`: The MCP server instance handling the request
  * `request_id::Union{RequestId,Nothing}`: The ID of the current request (if any)
  * `progress_token::Union{ProgressToken,Nothing}`: Optional token for progress reporting
