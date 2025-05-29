```julia
fbernoulli(x)

```

Bernoulli function $B(x)=\frac{x}{e^x-1}$ for exponentially fitted upwinding.

The name `fbernoulli` has been chosen to avoid confusion with `Bernoulli` from JuliaStats/Distributions.jl

Returns a real number containing the result.

While `x/expm1(x)`  appears to be sufficiently accurate for all `x!=0`,  it's derivative calculated via `ForwardDiff.jl` is not,  so we use the polynomial approximation in the   interval `(-bernoulli_small_threshold, bernoulli_small_threshold)`. 

Also, see the discussion in [#117](https://github.com/WIAS-PDELib/VoronoiFVM.jl/issues/117).
