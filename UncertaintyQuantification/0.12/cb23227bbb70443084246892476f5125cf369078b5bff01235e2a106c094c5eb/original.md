```
MaximumAPosterioriBayesian(prior, optimmethod, x0; islog, lowerbounds, upperbounds)
```

Passed to [`bayesianupdating`](@ref) to estimate one or more maxima of the posterior distribution starting from `x0`. The optimization uses the method specified in `optimmethod`. Will calculate one estimation per point in x0. The flag `islog` specifies whether the prior and likelihood functions passed to the  [`bayesianupdating`](@ref) method are already  given as logarithms. `lowerbounds` and `upperbounds` specify optimization intervals.

Alternative constructors

```julia
    MaximumAPosterioriBayesian(prior, optimmethod, x0; islog) # `lowerbounds` = [-Inf], # `upperbounds` = [Inf]
    MaximumAPosterioriBayesian(prior, optimmethod, x0)  # `islog` = true
```

See also [`MaximumLikelihoodBayesian`](@ref), [`bayesianupdating`](@ref),  [`TransitionalMarkovChainMonteCarlo`](@ref).
