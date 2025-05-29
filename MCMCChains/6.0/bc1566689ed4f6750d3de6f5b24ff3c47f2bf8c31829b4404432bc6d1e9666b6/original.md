```
cor(chains[; sections, append_chains = true, kwargs...])
```

Compute the Pearson correlation matrix for the chain.

Setting `append_chains=false` will return a vector of dataframes containing a correlation matrix for each chain.
