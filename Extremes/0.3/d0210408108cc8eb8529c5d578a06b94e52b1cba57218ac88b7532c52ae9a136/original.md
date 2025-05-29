```
quantile(fm::MaximumLikelihoodEVA, p::Real)::Vector{<:Real}
```

Compute the quantile of level `p` from the fitted model by maximum likelihood. In the case of non-stationarity, the effective quantiles are returned.
