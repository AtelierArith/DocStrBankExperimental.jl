```
apply_kraus_map!(::Quest,::TwoQubits,::TracePreserving,ρ,q,complex_mat,num_ops)
```

Applies a Kraus map to a density matrix for two qubits.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::TwoQubits`: Indicates that the operation is applied to two qubits.
  * `::TracePreserving`: Indicates that the operation is trace preserving.
  * `ρ::QuEST density matrix`: The density matrix to apply the operation to.
  * `q::Tuple{Int64, Int64}`: The qubits to apply the operation to.
  * `complex_mat::Array{ComplexF64, 4}`: The array of Kraus operators.
  * `num_ops::Int64`: The number of Kraus operators.

# Examples

```julia
num_qubits = 2
q = (1, 2)
num_ops = 4
complex_mat = Array{ComplexF64, 4}(undef, 2, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),TwoQubits(),TracePreserving(),ρ,q,complex_mat,num_ops)
```
