```julia
struct UA_PublishedEventTemplateConfig
```

Fields:

  * `metaData::Open62541.UA_DataSetMetaDataType`
  * `eventNotfier::Open62541.UA_NodeId`
  * `selectedFieldsSize::UInt64`
  * `selectedFields::Ptr{Open62541.UA_SimpleAttributeOperand}`
  * `filter::Open62541.UA_ContentFilter`
