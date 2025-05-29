```julia
struct UA_FindServersOnNetworkResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `lastCounterResetTime::Int64`
  * `serversSize::UInt64`
  * `servers::Ptr{Open62541.UA_ServerOnNetwork}`
