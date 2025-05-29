```julia
struct UA_AddNodesRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `nodesToAddSize::UInt64`
  * `nodesToAdd::Ptr{Open62541.UA_AddNodesItem}`
