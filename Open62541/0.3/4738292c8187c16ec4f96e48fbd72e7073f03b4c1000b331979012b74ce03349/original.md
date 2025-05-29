```julia
struct UA_SecurityGroupDataType
```

Fields:

  * `name::Open62541.UA_String`
  * `securityGroupFolderSize::UInt64`
  * `securityGroupFolder::Ptr{Open62541.UA_String}`
  * `keyLifetime::Float64`
  * `securityPolicyUri::Open62541.UA_String`
  * `maxFutureKeyCount::UInt32`
  * `maxPastKeyCount::UInt32`
  * `securityGroupId::Open62541.UA_String`
  * `rolePermissionsSize::UInt64`
  * `rolePermissions::Ptr{Open62541.UA_RolePermissionType}`
  * `groupPropertiesSize::UInt64`
  * `groupProperties::Ptr{Open62541.UA_KeyValuePair}`
