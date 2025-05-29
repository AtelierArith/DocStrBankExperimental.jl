```
JSONRPCResponse(; id::RequestId, result::Union{ResponseResult,Dict{String,Any}}) <: Response
```

JSON-RPC response message returned for successful requests.

# Fields

  * `id::RequestId`: Identifier matching the request this is responding to
  * `result::Union{ResponseResult,Dict{String,Any}}`: Results of the method execution
