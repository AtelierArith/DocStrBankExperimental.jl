```
fermionEmit(op, η_emit, γ_emit, η_absorb)
```

Generate fermionic bath which describes the emission process of the fermionic system by a correlation function $C^{\nu=-}$

# Parameters

  * `op::QuantumObject` : The system annihilation operator according to the system-fermionic-bath interaction.
  * `η_emit::Vector{Ti<:Number}` : the coefficients $\eta_i$ of emission bath correlation function $C^{\nu=-}$.
  * `γ_emit::Vector{Ti<:Number}` : the coefficients $\gamma_i$ of emission bath correlation function $C^{\nu=-}$.
  * `η_absorb::Vector{Ti<:Number}` : the coefficients $\eta_i$ of absorption bath correlation function $C^{\nu=+}$.
