```
add_dephasing!(::Quest,::TwoQubits,ρ,q,p)
```

Adds a dephasing noise model to a density matrix for two qubits.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::TwoQubits`: Indicates that the noise is applied to two qubits.
  * `ρ::QuEST density matrix`: The density matrix to apply the noise to.
  * `q::Tuple{Int64, Int64}`: The qubits to apply the noise to.
  * `p::Float64`: The probability of the noise.

# Examples

```julia
num_qubits = 2
q = (1, 2)
p = 0.3
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_dephasing!(Quest(),TwoQubits(),ρ,q,p)
```
