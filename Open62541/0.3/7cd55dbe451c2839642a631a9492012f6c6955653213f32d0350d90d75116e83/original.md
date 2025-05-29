```julia
struct UA_SecurityPolicy
```

Fields:

  * `policyContext::Ptr{Nothing}`
  * `policyUri::Open62541.UA_String`
  * `localCertificate::Open62541.UA_String`
  * `asymmetricModule::Open62541.UA_SecurityPolicyAsymmetricModule`
  * `symmetricModule::Open62541.UA_SecurityPolicySymmetricModule`
  * `certificateSigningAlgorithm::Open62541.UA_SecurityPolicySignatureAlgorithm`
  * `channelModule::Open62541.UA_SecurityPolicyChannelModule`
  * `logger::Ptr{Open62541.UA_Logger}`
  * `updateCertificateAndPrivateKey::Ptr{Nothing}`
  * `clear::Ptr{Nothing}`
