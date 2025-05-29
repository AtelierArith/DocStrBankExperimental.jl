```julia
struct ConstantCouplings <: OpenQuantumBase.AbstractCouplings
```

Defines constant system bath coupling operators.

# Fields

  * `mats`: 1-D array for independent coupling operators
  * `str_rep`: String representation for the coupling (for display purpose)
