```julia
struct VIDAProblem{D<:VIDA.AbstractDivergence, F, N, B}
```

A composite type that holds various properties that define the optimization process to extract the optimal filter.

## Fields

  * `div`: Divergence you will fit

  * `f`: Function that defines the parametric family of templates

  * `autodiff`: Type of autodiff to use when optimizing if any

  * `lb`: The lower bounds of the parameter ranges to search over

  * `ub`: The upper bounds of parameter ranges to search over
