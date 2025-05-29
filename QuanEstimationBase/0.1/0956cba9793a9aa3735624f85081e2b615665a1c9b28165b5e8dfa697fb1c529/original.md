```
LLD(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; rep="original", eps=GLOBAL_EPS) where {T<:Complex}
```

Calculate the left logarrithmic derivatives (LLDs). The LLD operator is defined as $\partial_{a}\rho=\mathcal{R}_a^{\dagger}\rho$, where ρ is the parameterized density matrix.    

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix with respect to the unknown parameters to be estimated. For example, drho[1] is the derivative vector with respect to the first parameter.
  * `rep`: Representation of the LLD operator. Options can be: "original" (default) and "eigen".
  * `eps`: Machine epsilon.
