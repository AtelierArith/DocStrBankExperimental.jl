```julia
struct UA_UpdateDataDetails
```

Fields:

  * `nodeId::Open62541.UA_NodeId`
  * `performInsertReplace::Open62541.UA_PerformUpdateType`
  * `updateValuesSize::UInt64`
  * `updateValues::Ptr{Open62541.UA_DataValue}`
