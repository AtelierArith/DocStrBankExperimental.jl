```julia
struct UA_FieldTargetDataType
```

フィールド:

  * `dataSetFieldId::Open62541.UA_Guid`
  * `receiverIndexRange::Open62541.UA_String`
  * `targetNodeId::Open62541.UA_NodeId`
  * `attributeId::UInt32`
  * `writeIndexRange::Open62541.UA_String`
  * `overrideValueHandling::Open62541.UA_OverrideValueHandling`
  * `overrideValue::Open62541.UA_Variant`
