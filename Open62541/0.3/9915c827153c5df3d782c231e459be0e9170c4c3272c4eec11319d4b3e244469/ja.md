```julia
struct UA_GetEndpointsRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `endpointUrl::Open62541.UA_String`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `profileUrisSize::UInt64`
  * `profileUris::Ptr{Open62541.UA_String}`
