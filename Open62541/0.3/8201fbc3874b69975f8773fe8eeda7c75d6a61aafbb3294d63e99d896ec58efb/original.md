```julia
struct UA_BrowseNextRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `releaseContinuationPoints::Bool`
  * `continuationPointsSize::UInt64`
  * `continuationPoints::Ptr{Open62541.UA_String}`
