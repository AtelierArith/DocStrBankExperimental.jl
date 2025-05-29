```
MaximumLikelihoodBayesian(prior, optimmethod, x0; islog, lowerbounds, upperbounds)
```

Passed to [`bayesianupdating`](@ref) to estimate one or more maxima of the likelihood starting from `x0`. The optimization uses the method specified in `optimmethod`. Will calculate one estimation per point in x0. The flag `islog` specifies whether the prior and likelihood functions passed to the  [`bayesianupdating`](@ref) method are already  given as logarithms. `lowerbounds` and `upperbounds` specify optimization intervals.

Alternative constructors

```julia
    MaximumLikelihoodBayesian(prior, optimmethod, x0; islog) # `lowerbounds` = [-Inf], # `upperbounds` = [Inf]
    MaximumLikelihoodBayesian(prior, optimmethod, x0)  # `islog` = true
```

### Notes

The method uses `prior` only as information on which parameters are supposed to be optimized. The prior itself does not influence the result of the maximum likelihood estimate and can be given as a dummy distribution. For example, if two parameters `a` and `b` are supposed to be optimized, the prior could look like this

```julia
    prior = RandomVariable.(Uniform(0,1), [:a, :b])
```

See also [`MaximumAPosterioriBayesian`](@ref), [`bayesianupdating`](@ref),  [`TransitionalMarkovChainMonteCarlo`](@ref).
