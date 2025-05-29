```julia
struct UA_DataSetReaderDataType
```

Fields:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `publisherId::Open62541.UA_Variant`
  * `writerGroupId::UInt16`
  * `dataSetWriterId::UInt16`
  * `dataSetMetaData::Open62541.UA_DataSetMetaDataType`
  * `dataSetFieldContentMask::UInt32`
  * `messageReceiveTimeout::Float64`
  * `keyFrameCount::UInt32`
  * `headerLayoutUri::Open62541.UA_String`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityGroupId::Open62541.UA_String`
  * `securityKeyServicesSize::UInt64`
  * `securityKeyServices::Ptr{Open62541.UA_EndpointDescription}`
  * `dataSetReaderPropertiesSize::UInt64`
  * `dataSetReaderProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `messageSettings::Open62541.UA_ExtensionObject`
  * `subscribedDataSet::Open62541.UA_ExtensionObject`
