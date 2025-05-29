```julia
struct UA_RegisterNodesRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `nodesToRegisterSize::UInt64`
  * `nodesToRegister::Ptr{Open62541.UA_NodeId}`
