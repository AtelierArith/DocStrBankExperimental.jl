```julia
struct UA_SecurityPolicySymmetricModule
```

フィールド:

  * `generateKey::Ptr{Nothing}`
  * `generateNonce::Ptr{Nothing}`
  * `secureChannelNonceLength::UInt64`
  * `cryptoModule::Open62541.UA_SecurityPolicyCryptoModule`
