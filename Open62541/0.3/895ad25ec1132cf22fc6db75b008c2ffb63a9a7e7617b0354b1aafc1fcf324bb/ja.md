```julia
struct UA_TranslateBrowsePathsToNodeIdsResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `resultsSize::UInt64`
  * `results::Ptr{Open62541.UA_BrowsePathResult}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
