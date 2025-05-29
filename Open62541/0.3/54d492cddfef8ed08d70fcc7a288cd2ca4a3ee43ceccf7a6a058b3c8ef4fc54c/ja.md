```julia
struct UA_FindServersRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `endpointUrl::Open62541.UA_String`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `serverUrisSize::UInt64`
  * `serverUris::Ptr{Open62541.UA_String}`
