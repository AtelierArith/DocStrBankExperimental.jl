```julia
struct UA_ClientConfig
```

フィールド:

  * `clientContext::Ptr{Nothing}`
  * `logging::Ptr{Open62541.UA_Logger}`
  * `timeout::UInt32`
  * `clientDescription::Open62541.UA_ApplicationDescription`
  * `endpointUrl::Open62541.UA_String`
  * `userIdentityToken::Open62541.UA_ExtensionObject`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityPolicyUri::Open62541.UA_String`
  * `noSession::Bool`
  * `noReconnect::Bool`
  * `noNewSession::Bool`
  * `endpoint::Open62541.UA_EndpointDescription`
  * `userTokenPolicy::Open62541.UA_UserTokenPolicy`
  * `applicationUri::Open62541.UA_String`
  * `customDataTypes::Ptr{Open62541.UA_DataTypeArray}`
  * `secureChannelLifeTime::UInt32`
  * `requestedSessionTimeout::UInt32`
  * `localConnectionConfig::Open62541.UA_ConnectionConfig`
  * `connectivityCheckInterval::UInt32`
  * `eventLoop::Ptr{Open62541.UA_EventLoop}`
  * `externalEventLoop::Bool`
  * `securityPoliciesSize::UInt64`
  * `securityPolicies::Ptr{Open62541.UA_SecurityPolicy}`
  * `certificateVerification::Open62541.UA_CertificateVerification`
  * `authSecurityPoliciesSize::UInt64`
  * `authSecurityPolicies::Ptr{Open62541.UA_SecurityPolicy}`
  * `authSecurityPolicyUri::Open62541.UA_String`
  * `stateCallback::Ptr{Nothing}`
  * `inactivityCallback::Ptr{Nothing}`
  * `outStandingPublishRequests::UInt16`
  * `subscriptionInactivityCallback::Ptr{Nothing}`
  * `sessionName::Open62541.UA_String`
  * `sessionLocaleIds::Ptr{Open62541.UA_String}`
  * `sessionLocaleIdsSize::UInt64`
  * `privateKeyPasswordCallback::Ptr{Nothing}`
