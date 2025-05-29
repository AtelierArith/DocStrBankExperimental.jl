```
apply_kraus_map!(::Quest,::SingleQubit,::TracePreserving,ρ,q,complex_mat,num_ops)
```

Applies a Kraus map to a density matrix for a single qubit.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::SingleQubit`: Indicates that the operation is applied to a single qubit.
  * `::TracePreserving`: Indicates that the operation is trace preserving.
  * `ρ::QuEST density matrix`: The density matrix to apply the operation to.
  * `q::Int64`: The qubit to apply the operation to.
  * `complex_mat::Array{ComplexF64, 3}`: The array of Kraus operators.
  * `num_ops::Int64`: The number of Kraus operators.

# Examples

```julia
num_qubits = 1
q = 1
num_ops = 2
complex_mat = Array{ComplexF64, 3}(undef, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),SingleQubit(),TracePreserving(),ρ,q,complex_mat,num_ops)
```
