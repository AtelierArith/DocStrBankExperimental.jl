```
autocor(
    chains;
    append_chains = true,
    demean = true,
    [lags,]
    kwargs...,
)
```

Compute the autocorrelation of each parameter for the chain.

The default `lags` are `[1, 5, 10, 50]`, upper-bounded by `n - 1` where `n` is the number of samples used in the estimation.

Setting `append_chains=false` will return a vector of dataframes containing the autocorrelations for each chain.
