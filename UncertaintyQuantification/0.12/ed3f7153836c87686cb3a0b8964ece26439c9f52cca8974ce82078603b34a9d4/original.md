```
SingleComponentMetropolisHastings(proposal, x0, n, burnin, islog)
```

Passed to [`bayesianupdating`](@ref) to run the single-component Metropolis-Hastings algorithm starting from `x0` with  univariate proposal distibution `proposal`. Will generate `n` samples *after* performing `burnin` steps of the Markov chain and discarding the samples. The flag `islog` specifies whether the prior and likelihood functions passed to the  [`bayesianupdating`](@ref) method are already  given as logarithms.

Alternative constructor

```julia
    SingleComponentMetropolisHastings(proposal, x0, n, burnin)  # `islog` = true
```
