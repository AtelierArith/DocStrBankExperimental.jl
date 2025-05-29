```
Circuit{N}(gates::Vector{<:CircuitGate}, mops::Union{Vector{<:MeasurementOperator},Nothing}=nothing)
```

`N`量子ビットの回路内の量子回路ゲートのチェーン。`CircuitGate`オブジェクトのベクターから構築されます。
