```
bosonRealImag(op, η_real, η_imag, γ)
```

Generate bosonic bath which the real part and imaginary part of the bath correlation function are combined

# Parameters

  * `op::QuantumObject` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `η_real::Vector{Ti<:Number}` : the real part of coefficients $\eta_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
  * `η_imag::Vector{Tj<:Number}` : the imaginary part of coefficients $\eta_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
  * `γ::Vector{Tk<:Number}` : the coefficients $\gamma_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
