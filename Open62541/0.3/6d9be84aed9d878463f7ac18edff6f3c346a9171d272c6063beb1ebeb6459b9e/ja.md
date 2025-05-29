```julia
struct UA_ReferenceDescription
```

フィールド:

  * `referenceTypeId::Open62541.UA_NodeId`
  * `isForward::Bool`
  * `nodeId::Open62541.UA_ExpandedNodeId`
  * `browseName::Open62541.UA_QualifiedName`
  * `displayName::Open62541.UA_LocalizedText`
  * `nodeClass::Open62541.UA_NodeClass`
  * `typeDefinition::Open62541.UA_ExpandedNodeId`
