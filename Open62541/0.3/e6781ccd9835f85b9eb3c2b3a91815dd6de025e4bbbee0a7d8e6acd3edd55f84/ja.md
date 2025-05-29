```julia
struct UA_OpenSecureChannelResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `serverProtocolVersion::UInt32`
  * `securityToken::Open62541.UA_ChannelSecurityToken`
  * `serverNonce::Open62541.UA_String`
