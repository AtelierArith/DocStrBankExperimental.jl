```julia
struct UA_EventFieldList
```

Fields:

  * `clientHandle::UInt32`
  * `eventFieldsSize::UInt64`
  * `eventFields::Ptr{Open62541.UA_Variant}`
