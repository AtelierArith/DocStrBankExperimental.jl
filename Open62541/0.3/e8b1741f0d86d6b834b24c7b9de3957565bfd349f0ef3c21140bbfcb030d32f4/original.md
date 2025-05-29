```julia
struct UA_DeleteNodesRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `nodesToDeleteSize::UInt64`
  * `nodesToDelete::Ptr{Open62541.UA_DeleteNodesItem}`
