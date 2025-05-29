```
densratio(x_nu, x_de, dre; [optlib])
```

Estimate density ratio `p_nu(x_de) / p_de(x_de)` with estimator `dre` and indexable collections of numerator and denominator samples, `x_nu` and `x_de`.

Optionally choose an optimization library `optlib` from the list below:

  * `JuliaLib`  - Pure Julia implementation
  * `OptimLib`  - Implementation with Optim.jl
  * `ConvexLib` - Implementation with Convex.jl
  * `JuMPLib`   - Implementation with JuMP.jl

See also [`densratiofunc`](@ref).
