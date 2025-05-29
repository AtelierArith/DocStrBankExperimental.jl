```
ToolMessage
```

A message type for tool calls. 

It represents both the request (fields `args`, `name`) and the response (field `content`).

# Fields

  * `content::Any`: The content of the message.
  * `req_id::Union{Nothing, Int}`: The unique ID of the request.
  * `tool_call_id::String`: The unique ID of the tool call.
  * `raw::AbstractString`: The raw JSON string of the tool call request.
  * `args::Union{Nothing, Dict{Symbol, Any}}`: The arguments of the tool call request.
  * `name::Union{Nothing, String}`: The name of the tool call request.
