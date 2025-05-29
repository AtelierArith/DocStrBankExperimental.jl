```julia
pfmeasurements(
    register::QuantumClifford.Register,
    frame::QuantumClifford.PauliFrame
) -> Any

```

指定された [`Register`](@ref) から参照測定を取得し、[`PauliFrame`](@ref) によって規定されたフリップを適用します。結果は各フレームの実際の（非相対的な）測定結果です。
