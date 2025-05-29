```julia
struct UA_BrowseDescription
```

Fields:

  * `nodeId::Open62541.UA_NodeId`
  * `browseDirection::Open62541.UA_BrowseDirection`
  * `referenceTypeId::Open62541.UA_NodeId`
  * `includeSubtypes::Bool`
  * `nodeClassMask::UInt32`
  * `resultMask::UInt32`
