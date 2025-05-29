```
TransitionalMarkovChainMonteCarlo(prior, n, burnin, β, islog)

Passed to [`bayesianupdating`](@ref) to run thetransitional Markov chain Monte Carlo algorithm  with [`RandomVariable'](@ref) vector `prior`. At each transitional level, one sample will be generated from `n` independent Markov chains after `burnin` steps have been discarded. The flag `islog` specifies whether the prior and likelihood functions passed to the  [`bayesianupdating`](@ref) method are already  given as logarithms.
```

Alternative constructors

```julia
    TransitionalMarkovChainMonteCarlo(prior, n, burnin, β)  # `islog` = true
     TransitionalMarkovChainMonteCarlo(prior, n, burnin)    # `β` = 0.2,  `islog` = true
```

# References

[chingTransitionalMarkovChain2007](@cite)
