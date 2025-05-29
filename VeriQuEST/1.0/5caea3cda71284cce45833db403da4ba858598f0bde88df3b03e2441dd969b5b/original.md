```
apply_kraus_map!(::Quest,::MultipleQubits,::TracePreserving,ρ,leas_sig_qubit,num_qubits,complex_mat,num_ops)
```

Applies a Kraus map to a density matrix for multiple qubits.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::MultipleQubits`: Indicates that the operation is applied to multiple qubits.
  * `::TracePreserving`: Indicates that the operation is trace preserving.
  * `ρ::QuEST density matrix`: The density matrix to apply the operation to.
  * `leas_sig_qubit::Int64`: The least significant qubit.
  * `num_qubits::Int64`: The number of qubits.
  * `complex_mat::Array{ComplexF64, 3}`: The array of Kraus operators.
  * `num_ops::Int64`: The number of Kraus operators.

# Examples

```julia
num_qubits = 3
leas_sig_qubit = 1
num_ops = 8
complex_mat = Array{ComplexF64, 3}(undef, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),MultipleQubits(),TracePreserving(),ρ,leas_sig_qubit,num_qubits,complex_mat,num_ops)
```
