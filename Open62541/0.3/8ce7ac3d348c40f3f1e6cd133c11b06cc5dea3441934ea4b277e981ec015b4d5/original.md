```julia
struct UA_EndpointDescription
```

Fields:

  * `endpointUrl::Open62541.UA_String`
  * `server::Open62541.UA_ApplicationDescription`
  * `serverCertificate::Open62541.UA_String`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityPolicyUri::Open62541.UA_String`
  * `userIdentityTokensSize::UInt64`
  * `userIdentityTokens::Ptr{Open62541.UA_UserTokenPolicy}`
  * `transportProfileUri::Open62541.UA_String`
  * `securityLevel::UInt8`
