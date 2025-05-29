```julia
struct UA_DeleteAtTimeDetails
```

Fields:

  * `nodeId::Open62541.UA_NodeId`
  * `reqTimesSize::UInt64`
  * `reqTimes::Ptr{Int64}`
