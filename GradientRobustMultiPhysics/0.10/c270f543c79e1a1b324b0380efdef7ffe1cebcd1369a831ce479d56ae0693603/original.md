```julia
abstract type AbstractFiniteElement
```

reconstruction identity operator: evaluates a reconstructed version of the finite element function.

FEreconst specifies the reconstruction space and reconstruction algorithm if it is defined for the finite element that it is applied to.
