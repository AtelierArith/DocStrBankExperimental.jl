```julia
struct UA_QueryNextRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `releaseContinuationPoint::Bool`
  * `continuationPoint::Open62541.UA_String`
