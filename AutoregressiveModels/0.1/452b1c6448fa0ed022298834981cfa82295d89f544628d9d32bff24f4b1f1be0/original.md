```
fit(::Type{<:Factor}, data, names, fonames, nfac::Integer; kwargs...)
```

Fit a factor model with `nfac` factors using variables indexed by `names` from a `Tables.jl`-compatible `data` table. Factors that are observed are specified with `fonames` as indices of columns from `data`. R-squared for each variable is computed based on standardized data with zero mean and unit standard deviation. See also [`Factor`](@ref) and [`fit!`](@ref).

# Keywords

  * `subset::Union{BitVector, Nothing}=nothing`: subset of `data` to be used for estimation.
  * `TF::Type=Float64`: numeric type used for estimation.
  * `svdalg::Algorithm=DivideAndConquer()`: algorithm for singular value decomposition.
  * `maxiter::Integer=10000`: maximum number of iterations; only relevant when the model involves both observed and unobserved factors.
  * `tol::Real=1e-8`: tolerance level for convergence; only relevant when the model involves both observed and unobserved factors.

# Reference

**Stock, James H. and Mark W. Watson.** 2016. "Chapter 8–-Dynamic Factor Models, Factor-Augmented Vector Autoregressions, and Structural Vector Autoregressions in Macroeconomics." In *Handbook of Macroeconomics*, Vol. 2A, edited by John B. Taylor and Harald Uhlig, 415–525. Amsterdam: Elsevier.
