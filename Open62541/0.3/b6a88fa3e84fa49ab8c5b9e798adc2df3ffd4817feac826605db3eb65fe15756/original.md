```julia
struct UA_RegisteredServer
```

Fields:

  * `serverUri::Open62541.UA_String`
  * `productUri::Open62541.UA_String`
  * `serverNamesSize::UInt64`
  * `serverNames::Ptr{Open62541.UA_LocalizedText}`
  * `serverType::Open62541.UA_ApplicationType`
  * `gatewayServerUri::Open62541.UA_String`
  * `discoveryUrlsSize::UInt64`
  * `discoveryUrls::Ptr{Open62541.UA_String}`
  * `semaphoreFilePath::Open62541.UA_String`
  * `isOnline::Bool`
