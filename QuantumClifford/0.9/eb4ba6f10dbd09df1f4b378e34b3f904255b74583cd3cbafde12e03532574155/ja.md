```julia
pfmeasurements(frame::QuantumClifford.PauliFrame) -> Any

```

[`PauliFrame`](@ref) インスタンス内の各フレームに対する測定結果を返します。

!!! warning "相対測定"
    返される測定値は基準測定に対して相対的であり、つまり、指定されたフレーム内で基準測定が反転したかどうかのみを示します。

