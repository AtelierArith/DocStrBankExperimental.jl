```
add_depolarising!(::Quest,::SingleQubit,ρ,q,p)
```

Adds a depolarising noise model to a density matrix for a single qubit.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::SingleQubit`: Indicates that the noise is applied to a single qubit.
  * `ρ::QuEST density matrix`: The density matrix to apply the noise to.
  * `q::Int64`: The qubit to apply the noise to.
  * `p::Float64`: The probability of the noise.

# Examples

```julia
num_qubits = 1
q = 1
p = 0.3
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_depolarising!(Quest(),SingleQubit(),ρ,q,p)
```
