```
struct bosonRealImag <: AbstractBosonBath
```

A bosonic bath which the real part and imaginary part of the bath correlation function are combined 

# Fields

  * `Comm`  : the super-operator (commutator) for the coupling operator.
  * `anComm`  : the super-operator (anti-commutator) for the coupling operator.
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `η_real` : the real part of coefficients $\eta_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
  * `η_imag` : the imaginary part of coefficients $\eta_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
  * `γ` : the coefficients $\gamma_i$ in bath correlation function $\sum_i \eta_i \exp(-\gamma_i t)$.
  * `Nterm` : the number of exponential-expansion term of correlation function.

!!! note "`dims` property"
    For a given `b::bosonRealImag`, `b.dims` or `getproperty(b, :dims)` returns its `dimensions` in the type of integer-vector.

