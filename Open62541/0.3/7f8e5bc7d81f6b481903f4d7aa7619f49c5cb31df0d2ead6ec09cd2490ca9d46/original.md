```julia
struct UA_DataSetWriterDataType
```

Fields:

  * `name::Open62541.UA_String`
  * `enabled::Bool`
  * `dataSetWriterId::UInt16`
  * `dataSetFieldContentMask::UInt32`
  * `keyFrameCount::UInt32`
  * `dataSetName::Open62541.UA_String`
  * `dataSetWriterPropertiesSize::UInt64`
  * `dataSetWriterProperties::Ptr{Open62541.UA_KeyValuePair}`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `messageSettings::Open62541.UA_ExtensionObject`
