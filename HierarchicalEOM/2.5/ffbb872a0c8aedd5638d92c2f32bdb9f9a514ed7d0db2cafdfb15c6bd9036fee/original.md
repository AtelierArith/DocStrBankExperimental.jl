```
struct bosonReal <: AbstractBosonBath
```

A bosonic bath for the real part of bath correlation function $C^{u=\textrm{R}}$

# Fields

  * `Comm`  : the super-operator (commutator) for the coupling operator.
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `η` : the coefficients $\eta_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
  * `γ` : the coefficients $\gamma_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
  * `Nterm` : the number of exponential-expansion term of correlation function.

!!! note "`dims` property"
    For a given `b::bosonReal`, `b.dims` or `getproperty(b, :dims)` returns its `dimensions` in the type of integer-vector.

