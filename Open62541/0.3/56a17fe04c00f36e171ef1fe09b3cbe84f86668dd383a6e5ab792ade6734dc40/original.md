```julia
struct UA_QueryFirstRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `view::Open62541.UA_ViewDescription`
  * `nodeTypesSize::UInt64`
  * `nodeTypes::Ptr{Open62541.UA_NodeTypeDescription}`
  * `filter::Open62541.UA_ContentFilter`
  * `maxDataSetsToReturn::UInt32`
  * `maxReferencesToReturn::UInt32`
