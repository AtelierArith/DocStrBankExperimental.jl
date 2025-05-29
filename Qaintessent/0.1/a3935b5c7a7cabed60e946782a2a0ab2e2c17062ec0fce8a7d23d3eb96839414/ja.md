```
Circuit{N}(gate::AbstractCircuitGate, mops::Union{Vector{<:MeasurementOperator},Nothing}=nothing)
```

`N`量子ビットの回路における量子回路ゲートのチェーン。`AbstractCircuitGate`オブジェクトのベクターから構築されます。
