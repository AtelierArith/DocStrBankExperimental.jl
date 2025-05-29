```julia
struct UA_PubSubKeyPushTargetDataType
```

Fields:

  * `applicationUri::Open62541.UA_String`
  * `pushTargetFolderSize::UInt64`
  * `pushTargetFolder::Ptr{Open62541.UA_String}`
  * `endpointUrl::Open62541.UA_String`
  * `securityPolicyUri::Open62541.UA_String`
  * `userTokenType::Open62541.UA_UserTokenPolicy`
  * `requestedKeyCount::UInt16`
  * `retryInterval::Float64`
  * `pushTargetPropertiesSize::UInt64`
  * `pushTargetProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `securityGroupsSize::UInt64`
  * `securityGroups::Ptr{Open62541.UA_String}`
