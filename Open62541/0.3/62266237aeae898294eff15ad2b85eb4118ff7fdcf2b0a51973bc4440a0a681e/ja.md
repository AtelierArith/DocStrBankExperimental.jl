```julia
struct UA_DataSetWriterConfig
```

フィールド:

  * `name::Open62541.UA_String`
  * `dataSetWriterId::UInt16`
  * `dataSetFieldContentMask::UInt32`
  * `keyFrameCount::UInt32`
  * `messageSettings::Open62541.UA_ExtensionObject`
  * `transportSettings::Open62541.UA_ExtensionObject`
  * `dataSetName::Open62541.UA_String`
  * `dataSetWriterProperties::Open62541.UA_KeyValueMap`
