```julia
struct UA_AxisInformation
```

Fields:

  * `engineeringUnits::Open62541.UA_EUInformation`
  * `eURange::Open62541.UA_Range`
  * `title::Open62541.UA_LocalizedText`
  * `axisScaleType::Open62541.UA_AxisScaleEnumeration`
  * `axisStepsSize::UInt64`
  * `axisSteps::Ptr{Float64}`
