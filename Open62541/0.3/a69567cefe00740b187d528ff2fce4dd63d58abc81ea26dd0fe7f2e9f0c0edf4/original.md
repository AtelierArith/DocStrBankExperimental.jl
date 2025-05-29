```julia
struct UA_ReadValueId
```

Fields:

  * `nodeId::Open62541.UA_NodeId`
  * `attributeId::UInt32`
  * `indexRange::Open62541.UA_String`
  * `dataEncoding::Open62541.UA_QualifiedName`
