```julia
struct UA_QueryDataSet
```

Fields:

  * `nodeId::Open62541.UA_ExpandedNodeId`
  * `typeDefinitionNode::Open62541.UA_ExpandedNodeId`
  * `valuesSize::UInt64`
  * `values::Ptr{Open62541.UA_Variant}`
