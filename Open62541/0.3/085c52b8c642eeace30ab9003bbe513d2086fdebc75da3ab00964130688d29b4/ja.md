```julia
struct UA_EventFieldList
```

フィールド:

  * `clientHandle::UInt32`
  * `eventFieldsSize::UInt64`
  * `eventFields::Ptr{Open62541.UA_Variant}`
