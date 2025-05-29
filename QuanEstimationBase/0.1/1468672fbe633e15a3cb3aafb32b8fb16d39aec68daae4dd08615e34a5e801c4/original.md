```
SLD(ρ::Matrix{T}, dρ::Vector{Matrix{T}}; rep="original", eps=GLOBAL_EPS) where {T<:Complex}
```

Calculate the symmetric logarrithmic derivatives (SLDs). The SLD operator $L_a$ is defined  as$\partial_{a}\rho=\frac{1}{2}(\rho L_{a}+L_{a}\rho)$, where $\rho$ is the parameterized density matrix. 

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix with respect to the unknown parameters to be estimated. For example, drho[1] is the derivative vector with respect to the first parameter.
  * `rep`: Representation of the SLD operator. Options can be: "original" (default) and "eigen" .
  * `eps`: Machine epsilon.
