```julia
struct UA_FindServersResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `serversSize::UInt64`
  * `servers::Ptr{Open62541.UA_ApplicationDescription}`
