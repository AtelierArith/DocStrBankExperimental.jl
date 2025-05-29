```
JSONRPCError(; id::Union{RequestId,Nothing}, error::ErrorInfo) <: Response
```

JSON-RPC error response message returned when requests fail.

# Fields

  * `id::Union{RequestId,Nothing}`: Identifier matching the request this is responding to, or null
  * `error::ErrorInfo`: Information about the error that occurred
