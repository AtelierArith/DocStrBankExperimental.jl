```
mixDamping(ρ::Array{Complex{Float64},2},q::Int64,p::Float64)
```

Mixes a damping noise model to a density matrix.

# Arguments

  * `ρ::QuEST density matrix`: The density matrix to apply the noise to
  * `q::Int64`: The qubit to apply the noise to
  * `p::Float64`: The probability of the noise

# Examples

```julia     num*qubits = 1 q = 1 p = 0.3 quantum*env = createQuESTEnv() ρ = createDensityQureg(num*qubits, quantum*env) add_damping!(Quest(),SingleQubit(),ρ,q,p)
