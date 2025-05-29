```julia
struct UA_AddReferencesItem
```

フィールド:

  * `sourceNodeId::Open62541.UA_NodeId`
  * `referenceTypeId::Open62541.UA_NodeId`
  * `isForward::Bool`
  * `targetServerUri::Open62541.UA_String`
  * `targetNodeId::Open62541.UA_ExpandedNodeId`
  * `targetNodeClass::Open62541.UA_NodeClass`
