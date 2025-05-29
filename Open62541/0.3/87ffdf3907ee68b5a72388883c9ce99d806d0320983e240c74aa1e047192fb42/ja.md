```julia
struct UA_AddNodesItem
```

フィールド:

  * `parentNodeId::Open62541.UA_ExpandedNodeId`
  * `referenceTypeId::Open62541.UA_NodeId`
  * `requestedNewNodeId::Open62541.UA_ExpandedNodeId`
  * `browseName::Open62541.UA_QualifiedName`
  * `nodeClass::Open62541.UA_NodeClass`
  * `nodeAttributes::Open62541.UA_ExtensionObject`
  * `typeDefinition::Open62541.UA_ExpandedNodeId`
