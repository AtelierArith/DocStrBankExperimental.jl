```julia
struct UA_SessionSecurityDiagnosticsDataType
```

Fields:

  * `sessionId::Open62541.UA_NodeId`
  * `clientUserIdOfSession::Open62541.UA_String`
  * `clientUserIdHistorySize::UInt64`
  * `clientUserIdHistory::Ptr{Open62541.UA_String}`
  * `authenticationMechanism::Open62541.UA_String`
  * `encoding::Open62541.UA_String`
  * `transportProtocol::Open62541.UA_String`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityPolicyUri::Open62541.UA_String`
  * `clientCertificate::Open62541.UA_String`
