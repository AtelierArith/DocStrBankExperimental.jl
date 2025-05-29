```
bosonEmit(op, η_emit, γ_emit, η_absorb)
```

Generate bosonic bath which describes the emission process of the bosonic system by a correlation function $C^{\nu=-}$

# Parameters

  * `op::QuantumObject` : The system annihilation operator according to the system-bosonic-bath interaction.
  * `η_emit::Vector{Ti<:Number}` : the coefficients $\eta_i$ of emission bath correlation function $C^{\nu=-}$.
  * `γ_emit::Vector{Ti<:Number}` : the coefficients $\gamma_i$ of emission bath correlation function $C^{\nu=-}$.
  * `η_absorb::Vector{Ti<:Number}` : the coefficients $\eta_i$ of absorption bath correlation function $C^{\nu=+}$.
