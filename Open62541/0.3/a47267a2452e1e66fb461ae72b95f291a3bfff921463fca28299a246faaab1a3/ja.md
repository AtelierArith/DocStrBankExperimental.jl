```julia
struct UA_DataValue
```

フィールド:

  * `value::Open62541.UA_Variant`
  * `sourceTimestamp::Int64`
  * `serverTimestamp::Int64`
  * `sourcePicoseconds::UInt16`
  * `serverPicoseconds::UInt16`
  * `status::UInt32`
  * `hasValue::Bool`
  * `hasStatus::Bool`
  * `hasSourceTimestamp::Bool`
  * `hasServerTimestamp::Bool`
  * `hasSourcePicoseconds::Bool`
  * `hasServerPicoseconds::Bool`
