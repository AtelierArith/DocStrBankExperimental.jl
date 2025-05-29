```julia
struct UA_BrowseResult
```

Fields:

  * `statusCode::UInt32`
  * `continuationPoint::Open62541.UA_String`
  * `referencesSize::UInt64`
  * `references::Ptr{Open62541.UA_ReferenceDescription}`
