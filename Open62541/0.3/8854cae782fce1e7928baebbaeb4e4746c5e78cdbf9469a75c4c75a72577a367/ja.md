```julia
struct UA_TranslateBrowsePathsToNodeIdsRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `browsePathsSize::UInt64`
  * `browsePaths::Ptr{Open62541.UA_BrowsePath}`
