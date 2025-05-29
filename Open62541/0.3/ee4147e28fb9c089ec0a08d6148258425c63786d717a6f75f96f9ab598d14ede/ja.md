```julia
struct UA_ApplicationDescription
```

フィールド:

  * `applicationUri::Open62541.UA_String`
  * `productUri::Open62541.UA_String`
  * `applicationName::Open62541.UA_LocalizedText`
  * `applicationType::Open62541.UA_ApplicationType`
  * `gatewayServerUri::Open62541.UA_String`
  * `discoveryProfileUri::Open62541.UA_String`
  * `discoveryUrlsSize::UInt64`
  * `discoveryUrls::Ptr{Open62541.UA_String}`
