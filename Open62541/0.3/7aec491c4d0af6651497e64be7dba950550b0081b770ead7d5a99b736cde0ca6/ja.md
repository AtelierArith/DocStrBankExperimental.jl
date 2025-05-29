```julia
struct UA_DeleteReferencesItem
```

フィールド:

  * `sourceNodeId::Open62541.UA_NodeId`
  * `referenceTypeId::Open62541.UA_NodeId`
  * `isForward::Bool`
  * `targetNodeId::Open62541.UA_ExpandedNodeId`
  * `deleteBidirectional::Bool`
