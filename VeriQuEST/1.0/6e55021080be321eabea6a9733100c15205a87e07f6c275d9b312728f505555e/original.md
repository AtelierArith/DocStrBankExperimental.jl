```
mix_two_density_matrices!(::Quest,::DensityMatrices,ρ₁,ρ₂,p)
```

Mixes two density matrices with a given probability.

# Arguments

  * `::Quest`: Indicates that this function is used in the context of a Quest environment.
  * `::DensityMatrices`: Indicates that the operation is applied to density matrices.
  * `ρ₁::QuEST density matrix`: The first density matrix.
  * `ρ₂::QuEST density matrix`: The second density matrix.
  * `p::Float64`: The probability of mixing.

# Examples

```julia
num_qubits = 2
quantum_env = createQuESTEnv()
ρ₁ = createDensityQureg(num_qubits, quantum_env)
ρ₂ = createDensityQureg(num_qubits, quantum_env)
p = 0.5
mix_two_density_matrices!(Quest(),DensityMatrices(),ρ₁,ρ₂,p)
```
