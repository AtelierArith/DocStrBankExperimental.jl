```julia
struct UA_PublishedDataSetDataType
```

フィールド:

  * `name::Open62541.UA_String`
  * `dataSetFolderSize::UInt64`
  * `dataSetFolder::Ptr{Open62541.UA_String}`
  * `dataSetMetaData::Open62541.UA_DataSetMetaDataType`
  * `extensionFieldsSize::UInt64`
  * `extensionFields::Ptr{Open62541.UA_KeyValuePair}`
  * `dataSetSource::Open62541.UA_ExtensionObject`
