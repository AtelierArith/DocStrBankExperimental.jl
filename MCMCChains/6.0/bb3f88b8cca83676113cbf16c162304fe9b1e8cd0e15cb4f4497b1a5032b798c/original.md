```
quantile(chains[; q = [0.025, 0.25, 0.5, 0.75, 0.975], append_chains = true, kwargs...])
```

Compute the quantiles for each parameter in the chain.

Setting `append_chains=false` will return a vector of dataframes containing the quantiles for each chain.
