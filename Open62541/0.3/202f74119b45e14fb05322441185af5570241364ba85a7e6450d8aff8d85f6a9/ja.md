```julia
struct UA_BrowseRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `view::Open62541.UA_ViewDescription`
  * `requestedMaxReferencesPerNode::UInt32`
  * `nodesToBrowseSize::UInt64`
  * `nodesToBrowse::Ptr{Open62541.UA_BrowseDescription}`
