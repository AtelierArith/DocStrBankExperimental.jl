```julia
struct UA_AliasNameDataType
```

Fields:

  * `aliasName::Open62541.UA_QualifiedName`
  * `referencedNodesSize::UInt64`
  * `referencedNodes::Ptr{Open62541.UA_ExpandedNodeId}`
