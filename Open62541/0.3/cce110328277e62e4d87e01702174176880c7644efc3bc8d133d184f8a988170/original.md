```julia
struct UA_ServerOnNetwork
```

Fields:

  * `recordId::UInt32`
  * `serverName::Open62541.UA_String`
  * `discoveryUrl::Open62541.UA_String`
  * `serverCapabilitiesSize::UInt64`
  * `serverCapabilities::Ptr{Open62541.UA_String}`
