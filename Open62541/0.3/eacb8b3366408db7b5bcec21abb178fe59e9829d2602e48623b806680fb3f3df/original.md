```julia
struct UA_PublishResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `subscriptionId::UInt32`
  * `availableSequenceNumbersSize::UInt64`
  * `availableSequenceNumbers::Ptr{UInt32}`
  * `moreNotifications::Bool`
  * `notificationMessage::Open62541.UA_NotificationMessage`
  * `resultsSize::UInt64`
  * `results::Ptr{UInt32}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
