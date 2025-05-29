```
struct bosonImag <: AbstractBosonBath
```

A bosonic bath for the imaginary part of bath correlation function $C^{u=\textrm{I}}$

# Fields

  * `Comm`  : the super-operator (commutator) for the coupling operator.
  * `anComm`  : the super-operator (anti-commutator) for the coupling operator.
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `η` : the coefficients $\eta_i$ in imaginary part of bath correlation function $C^{u=\textrm{I}}$.
  * `γ` : the coefficients $\gamma_i$ in imaginary part of bath correlation function $C^{u=\textrm{I}}$.
  * `Nterm` : the number of exponential-expansion term of correlation function.

!!! note "`dims` property"
    For a given `b::bosonImag`, `b.dims` or `getproperty(b, :dims)` returns its `dimensions` in the type of integer-vector.

