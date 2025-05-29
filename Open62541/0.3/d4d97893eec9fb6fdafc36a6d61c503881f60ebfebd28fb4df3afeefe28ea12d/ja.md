```julia
struct UA_RegisterNodesResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `registeredNodeIdsSize::UInt64`
  * `registeredNodeIds::Ptr{Open62541.UA_NodeId}`
