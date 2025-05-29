```julia
struct UA_PublishedEventsDataType
```

Fields:

  * `eventNotifier::Open62541.UA_NodeId`
  * `selectedFieldsSize::UInt64`
  * `selectedFields::Ptr{Open62541.UA_SimpleAttributeOperand}`
  * `filter::Open62541.UA_ContentFilter`
