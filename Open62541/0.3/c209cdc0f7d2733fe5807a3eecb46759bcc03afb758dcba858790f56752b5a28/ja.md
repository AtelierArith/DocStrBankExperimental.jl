```julia
struct UA_WriteValue
```

フィールド:

  * `nodeId::Open62541.UA_NodeId`
  * `attributeId::UInt32`
  * `indexRange::Open62541.UA_String`
  * `value::Open62541.UA_DataValue`
