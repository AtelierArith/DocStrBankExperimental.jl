```julia
struct UA_PubSubConfiguration2DataType
```

Fields:

  * `publishedDataSetsSize::UInt64`
  * `publishedDataSets::Ptr{Open62541.UA_PublishedDataSetDataType}`
  * `connectionsSize::UInt64`
  * `connections::Ptr{Open62541.UA_PubSubConnectionDataType}`
  * `enabled::Bool`
  * `subscribedDataSetsSize::UInt64`
  * `subscribedDataSets::Ptr{Open62541.UA_StandaloneSubscribedDataSetDataType}`
  * `dataSetClassesSize::UInt64`
  * `dataSetClasses::Ptr{Open62541.UA_DataSetMetaDataType}`
  * `defaultSecurityKeyServicesSize::UInt64`
  * `defaultSecurityKeyServices::Ptr{Open62541.UA_EndpointDescription}`
  * `securityGroupsSize::UInt64`
  * `securityGroups::Ptr{Open62541.UA_SecurityGroupDataType}`
  * `pubSubKeyPushTargetsSize::UInt64`
  * `pubSubKeyPushTargets::Ptr{Open62541.UA_PubSubKeyPushTargetDataType}`
  * `configurationVersion::UInt32`
  * `configurationPropertiesSize::UInt64`
  * `configurationProperties::Ptr{Open62541.UA_KeyValuePair}`
