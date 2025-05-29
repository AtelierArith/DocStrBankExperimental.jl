```
bosonImag(op, η_imag, γ_imag)
```

Generate bosonic bath for the imaginary part of correlation function $C^{u=\textrm{I}}$

# Parameters

  * `op::QuantumObject` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `η_imag::Vector{Ti<:Number}` : the coefficients $\eta_i$ in imaginary part of bath correlation functions $C^{u=\textrm{I}}$.
  * `γ_imag::Vector{Tj<:Number}` : the coefficients $\gamma_i$ in imaginary part of bath correlation functions $C^{u=\textrm{I}}$.
