```julia
PauliFrame(
    frames,
    qubits,
    measurements
) -> QuantumClifford.PauliFrame{QuantumClifford.Stabilizer{QuantumClifford.Tableau{Vector{UInt8}, LinearAlgebra.Adjoint{UInt64, Matrix{UInt64}}}}}

```

Prepare an empty set of Pauli frames with the given number of `frames` and `qubits`. Preallocates spaces for `measurement` number of measurements.
