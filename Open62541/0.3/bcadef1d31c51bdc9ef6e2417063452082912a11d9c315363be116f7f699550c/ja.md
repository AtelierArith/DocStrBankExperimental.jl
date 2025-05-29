```julia
struct UA_AddReferencesRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `referencesToAddSize::UInt64`
  * `referencesToAdd::Ptr{Open62541.UA_AddReferencesItem}`
