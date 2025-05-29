```
DifferentialInfoEstimator
```

The supertype of all differential information measure estimators. These estimators compute an information measure in various ways that do not involve explicitly estimating a probability distribution.

Each [`DifferentialInfoEstimator`](@ref)s uses a specialized technique to approximate relevant densities/integrals, and is often tailored to one or a few types of information measures. For example, [`Kraskov`](@ref) estimates the [`Shannon`](@ref) entropy.

See [`information`](@ref) for usage.

## Implementations

  * [`KozachenkoLeonenko`](@ref).
  * [`Kraskov`](@ref).
  * [`Goria`](@ref).
  * [`Gao`](@ref).
  * [`Zhu`](@ref)
  * [`ZhuSingh`](@ref).
  * [`Lord`](@ref).
  * [`AlizadehArghami`](@ref).
  * [`Correa`](@ref).
  * [`Vasicek`](@ref).
  * [`Ebrahimi`](@ref).
  * [`LeonenkoProzantoSavani`](@ref).
