```julia
struct UA_StandaloneSubscribedDataSetDataType
```

Fields:

  * `name::Open62541.UA_String`
  * `dataSetFolderSize::UInt64`
  * `dataSetFolder::Ptr{Open62541.UA_String}`
  * `dataSetMetaData::Open62541.UA_DataSetMetaDataType`
  * `subscribedDataSet::Open62541.UA_ExtensionObject`
