```julia
struct UA_OpenSecureChannelRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `clientProtocolVersion::UInt32`
  * `requestType::Open62541.UA_SecurityTokenRequestType`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `clientNonce::Open62541.UA_String`
  * `requestedLifetime::UInt32`
