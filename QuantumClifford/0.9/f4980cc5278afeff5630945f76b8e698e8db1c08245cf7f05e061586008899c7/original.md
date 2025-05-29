```julia
pftrajectories(
    register::QuantumClifford.Register,
    circuit;
    trajectories
) -> Tuple{QuantumClifford.Register, QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}, Matrix{Bool}}}

```

For a given [`Register`](@ref) and circuit, simulates the reference circuit acting on the register and then also simulate numerous [`PauliFrame`](@ref) trajectories. Returns the register and the [`PauliFrame`](@ref) instance.

Use [`pfmeasurements`](@ref) to get the measurement results.
