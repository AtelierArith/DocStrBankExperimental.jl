```julia
pftrajectories(
    circuit;
    trajectories,
    threads
) -> QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}, Matrix{Bool}}

```

The main method for running Pauli frame simulations of circuits. See the other methods for lower level access.

Multithreading is enabled by default, but can be disabled by setting `threads=false`. Do not forget to launch Julia with multiple threads enabled, e.g. `julia -t4`, if you want to use multithreading.

See also: [`mctrajectories`](@ref), [`petrajectories`](@ref)
