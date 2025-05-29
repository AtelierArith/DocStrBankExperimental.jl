```julia
pfmeasurements(frame::QuantumClifford.PauliFrame) -> Any

```

Returns the measurement results for each frame in the [`PauliFrame`](@ref) instance.

!!! warning "Relative measurements"
    The return measurements are relative to the reference measurements, i.e. they only say whether the reference measurements have been flipped in the given frame.

