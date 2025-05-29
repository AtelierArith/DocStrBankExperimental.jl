```
bosonReal(op, η_real, γ_real)
```

Generate bosonic bath for the real part of bath correlation function $C^{u=\textrm{R}}$

# Parameters

  * `op::QuantumObject` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `η_real::Vector{Ti<:Number}` : the coefficients $\eta_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
  * `γ_real::Vector{Tj<:Number}` : the coefficients $\gamma_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
