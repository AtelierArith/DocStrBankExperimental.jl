```julia
struct UA_TransferResult
```

Fields:

  * `statusCode::UInt32`
  * `availableSequenceNumbersSize::UInt64`
  * `availableSequenceNumbers::Ptr{UInt32}`
