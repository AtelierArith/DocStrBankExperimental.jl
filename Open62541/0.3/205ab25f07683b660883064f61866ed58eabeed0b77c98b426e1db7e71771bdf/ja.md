```julia
struct UA_UnregisterNodesRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `nodesToUnregisterSize::UInt64`
  * `nodesToUnregister::Ptr{Open62541.UA_NodeId}`
