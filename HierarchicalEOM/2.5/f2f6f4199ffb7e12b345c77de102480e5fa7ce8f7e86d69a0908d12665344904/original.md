```
bosonAbsorb(op, η_absorb, γ_absorb, η_emit)
```

Generate bosonic bath which describes the absorption process of the bosonic system by a correlation function $C^{\nu=+}$

# Parameters

  * `op::QuantumObject` : The system creation operator according to the system-fermionic-bath interaction.
  * `η_absorb::Vector{Ti<:Number}` : the coefficients $\eta_i$ of absorption bath correlation function $C^{\nu=+}$.
  * `γ_absorb::Vector{Tj<:Number}` : the coefficients $\gamma_i$ of absorption bath correlation function $C^{\nu=+}$.
  * `η_emit::Vector{Tk<:Number}` : the coefficients $\eta_i$ of emission bath correlation function $C^{\nu=-}$.
