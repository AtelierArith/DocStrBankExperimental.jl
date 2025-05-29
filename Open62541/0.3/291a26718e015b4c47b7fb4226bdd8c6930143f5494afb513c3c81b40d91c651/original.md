```julia
struct UA_SessionlessInvokeRequestType
```

Fields:

  * `urisVersion::UInt32`
  * `namespaceUrisSize::UInt64`
  * `namespaceUris::Ptr{Open62541.UA_String}`
  * `serverUrisSize::UInt64`
  * `serverUris::Ptr{Open62541.UA_String}`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `serviceId::UInt32`
