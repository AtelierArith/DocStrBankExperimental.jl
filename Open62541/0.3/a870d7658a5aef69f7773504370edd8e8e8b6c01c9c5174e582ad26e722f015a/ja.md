```julia
struct UA_NotificationMessage
```

フィールド:

  * `sequenceNumber::UInt32`
  * `publishTime::Int64`
  * `notificationDataSize::UInt64`
  * `notificationData::Ptr{Open62541.UA_ExtensionObject}`
