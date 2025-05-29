```julia
pfmeasurements(
    register::QuantumClifford.Register,
    frame::QuantumClifford.PauliFrame
) -> Any

```

Takes the references measurements from the given [`Register`](@ref) and applies the flips as prescribed by the [`PauliFrame`](@ref) relative measurements. The result is the actual (non-relative) measurement results for each frame.
