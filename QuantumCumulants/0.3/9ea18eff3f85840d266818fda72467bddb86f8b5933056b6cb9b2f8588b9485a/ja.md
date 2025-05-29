```
numeric_average(avg::Average, state; level_map = nothing)
numeric_average(q::QNumber, state; level_map = nothing)
```

シンボリック平均 `avg` または演算子 `q` から、与えられた量子状態 `state` に対する対応する数値平均値を計算します。この状態は `QuantumOpticsBase.StateVector` または `QuantumOpticsBase.Operator` のいずれかの型であることができます。

参照: [`initial_values`](@ref), [`to_numeric`](@ref)
