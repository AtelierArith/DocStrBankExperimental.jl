```julia
struct UA_SimpleAttributeOperand
```

Fields:

  * `typeDefinitionId::Open62541.UA_NodeId`
  * `browsePathSize::UInt64`
  * `browsePath::Ptr{Open62541.UA_QualifiedName}`
  * `attributeId::UInt32`
  * `indexRange::Open62541.UA_String`
