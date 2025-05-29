```julia
pftrajectories(
    state::QuantumClifford.PauliFrame,
    circuit
) -> QuantumClifford.PauliFrame

```

Evolve each frame stored in [`PauliFrame`](@ref) by the given circuit.
