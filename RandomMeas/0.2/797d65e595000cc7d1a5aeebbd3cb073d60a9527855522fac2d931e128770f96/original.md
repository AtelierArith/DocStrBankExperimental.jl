```
get_expect_shadow(O::MPO, measurement_data::MeasurementData{ShallowUnitaryMeasurementSetting}, inverse_shallow_map::Vector{ITensor},s::Vector{Index{Int64}},ξ::Vector{Index{Int64}})
```

Compute the expectation value of an MPO operator `O` from a shallow MeasurementData and and inverse shallow_map

# Returns:

The expectation value as a `ComplexF64` (or `Float64` if purely real).
