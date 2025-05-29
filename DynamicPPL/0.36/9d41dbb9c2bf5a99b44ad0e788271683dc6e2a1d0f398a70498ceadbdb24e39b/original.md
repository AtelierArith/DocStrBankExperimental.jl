```
pointwise_prior_logdensities(model, chain[, keytype, context])
```

Compute the pointwise log-prior-densities of the model given the chain. This is the same as `pointwise_logdensities(model, chain, context)`, but only including the prior terms. See also: [`pointwise_logdensities`](@ref).
