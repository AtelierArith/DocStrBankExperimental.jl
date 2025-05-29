```
pointwise_loglikelihoods(model, chain[, keytype, context])
```

Compute the pointwise log-likelihoods of the model given the chain. This is the same as `pointwise_logdensities(model, chain, context)`, but only including the likelihood terms. See also: [`pointwise_logdensities`](@ref).
