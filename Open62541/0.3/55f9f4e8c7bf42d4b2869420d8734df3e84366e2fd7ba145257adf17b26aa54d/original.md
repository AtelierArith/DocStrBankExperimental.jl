```julia
struct UA_WriterGroupDataType
```

Fields:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `securityMode::Open62541.UA_MessageSecurityMode`
  * `securityGroupId::Open62541.UA_String`
  * `securityKeyServicesSize::UInt64`
  * `securityKeyServices::Ptr{Open62541.UA_EndpointDescription}`
  * `maxNetworkMessageSize::UInt32`
  * `groupPropertiesSize::UInt64`
  * `groupProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `writerGroupId::UInt16`
  * `publishingInterval::Float64`
  * `keepAliveTime::Float64`
  * `priority::UInt8`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `headerLayoutUri::Open62541.UA_String`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `messageSettings::Open62541.UA_ExtensionObject`
  * `dataSetWritersSize::UInt64`
  * `dataSetWriters::Ptr{Open62541.UA_DataSetWriterDataType}`
