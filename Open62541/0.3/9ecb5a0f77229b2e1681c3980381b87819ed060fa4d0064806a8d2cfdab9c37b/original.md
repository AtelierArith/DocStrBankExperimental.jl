```julia
struct UA_RegisterServer2Request
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `server::Open62541.UA_RegisteredServer`
  * `discoveryConfigurationSize::UInt64`
  * `discoveryConfiguration::Ptr{Open62541.UA_ExtensionObject}`
