```
get_expect_shadow(O::MPO, measurement_data::MeasurementData{ShallowUnitaryMeasurementSetting}, inverse_shallow_map::Vector{ITensor},s::Vector{Index{Int64}},ξ::Vector{Index{Int64}})
```

MPO演算子`O`の期待値を浅いMeasurementDataと逆浅いマップから計算します。

# 戻り値:

期待値を`ComplexF64`（または純粋に実数の場合は`Float64`）として返します。
