```
initial_values(eqs::MeanfieldEquations, state; level_map=nothing)
```

一連の記号方程式 `eqs` に対して、システムの数値量子状態 `state` に対応する初期状態の平均値を計算します。量子状態は `QuantumOpticsBase.StateVector` または `QuantumOpticsBase.Operator` のいずれかの型であることができます。

参照: [`to_numeric`](@ref), [`numeric_average`](@ref)
