```
mutable struct QubitNoiseParameters <: NoiseParameters
```

Qubit noise parameters for a quantum system.

# Fields

  * `ρ::Union{DensityMatrix,Qureg}`: The density matrix or quantum register representing the state of the qubits.
  * `q::Union{Nothing,Vector{Int64},Int64,Vector{Int32},Int32}`: The indices of the qubits affected by the noise.
