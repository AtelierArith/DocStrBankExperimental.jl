```
struct fermionEmit <: AbstractFermionBath
```

An bath object which describes the emission process of the fermionic system by a correlation function $C^{\nu=-}$

# Fields

  * `spre`   : the super-operator (left side operator multiplication) for the coupling operator.
  * `spost`  : the super-operator (right side operator multiplication) for the coupling operator.
  * `spreD`  : the super-operator (left side operator multiplication) for the adjoint of the coupling operator.
  * `spostD` : the super-operator (right side operator multiplication) for the adjoint of the coupling operator.
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `η` : the coefficients $\eta_i$ of emission bath correlation function $C^{\nu=-}$.
  * `γ` : the coefficients $\gamma_i$ of emission bath correlation function $C^{\nu=-}$.
  * `η_absorb` : the coefficients $\eta_i$ of absorption bath correlation function $C^{\nu=+}$.
  * `Nterm` : the number of exponential-expansion term of correlation function.

!!! note "`dims` property"
    For a given `b::fermionEmit`, `b.dims` or `getproperty(b, :dims)` returns its `dimensions` in the type of integer-vector.

