```
struct KrausMapNoiseParameters <: NoiseParameters
```

The `KrausMapNoiseParameters` struct represents the noise parameters for a Kraus map noise model.

Fields:

  * `trace`: Union{TracePreserving,NotTracePreserving} - Specifies whether the noise is trace preserving or not.
  * `ρ`: Union{DensityMatrix,Qureg} - The density matrix or quantum register representing the initial state.
  * `q`: Union{Nothing,Vector{Int64},Int64,Vector{Int32},Int32} - The indices of the qubits affected by the noise.
  * `mat`: Matrix{ComplexF64} - The matrix representation of the Kraus operators.
  * `num_ops`: Union{Int32,Int64} - The number of Kraus operators.
  * `num_qubits`: Union{Nothing,Int64} - The number of qubits in the system.
