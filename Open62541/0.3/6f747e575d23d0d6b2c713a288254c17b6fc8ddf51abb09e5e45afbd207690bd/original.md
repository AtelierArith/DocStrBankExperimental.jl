```julia
struct UA_DeleteReferencesRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `referencesToDeleteSize::UInt64`
  * `referencesToDelete::Ptr{Open62541.UA_DeleteReferencesItem}`
