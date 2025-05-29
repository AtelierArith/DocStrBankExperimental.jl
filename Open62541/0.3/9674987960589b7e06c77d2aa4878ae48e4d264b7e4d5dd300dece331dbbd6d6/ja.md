```julia
struct UA_ReaderGroupDataType
```

フィールド:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityGroupId::Open62541.UA_String`
  * `securityKeyServicesSize::UInt64`
  * `securityKeyServices::Ptr{Open62541.UA_EndpointDescription}`
  * `maxNetworkMessageSize::UInt32`
  * `groupPropertiesSize::UInt64`
  * `groupProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `messageSettings::Open62541.UA_ExtensionObject`
  * `dataSetReadersSize::UInt64`
  * `dataSetReaders::Ptr{Open62541.UA_DataSetReaderDataType}`
