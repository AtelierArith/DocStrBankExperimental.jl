```
add_pauli_noise!(::Quest,::SingleQubit,ρ,q,p)
```

Adds a Pauli noise model to a density matrix for a single qubit.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::SingleQubit`: Indicates that the noise is applied to a single qubit.
  * `ρ::QuEST density matrix`: The density matrix to apply the noise to.
  * `q::Int64`: The qubit to apply the noise to.
  * `p::Tuple{Float64, Float64, Float64}`: The probabilities of the X, Y, and Z Pauli errors.

# Examples

```julia
num_qubits = 1
q = 1
p = (0.1, 0.2, 0.3)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_pauli_noise!(Quest(),SingleQubit(),ρ,q,p)
```
