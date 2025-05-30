```
function summarystats(
    chains;
    sections = _default_sections(chains),
    append_chains= true,
    autocov_method::AbstractAutocovMethod = AutocovMethod(),
    maxlag = 250,
    kwargs...
)
```

Compute the mean, standard deviation, Monte Carlo standard error, bulk- and tail- effective sample size, and $\widehat{R}$ diagnostic for each parameter in the chain.

Setting `append_chains=false` will return a vector of dataframes containing the summary statistics for each chain.

When estimating the effective sample size, autocorrelations are computed for at most `maxlag` lags.
