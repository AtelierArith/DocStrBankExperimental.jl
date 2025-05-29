```
Psis{R<:Real, AT<:AbstractArray{R, 3}, VT<:AbstractVector{R}}
```

A struct containing the results of Pareto-smoothed importance sampling.

# Fields

  * `weights`: A vector of smoothed, truncated, and normalized importance sampling weights.
  * `pareto_k`: Estimates of the shape parameter `k` of the generalized Pareto distribution.
  * `ess`: Estimated effective sample size for each LOO evaluation, based on the variance of the weights.
  * `sup_ess`: Estimated effective sample size for each LOO evaluation, based on the  supremum norm, i.e. the size of the largest weight. More likely than `ess` to warn when  importance sampling has failed. However, it can have a high variance.
  * `r_eff`: The relative efficiency of the MCMC chain, i.e. ESS / posterior sample size.
  * `tail_len`: Vector indicating how large the "tail" is for each observation.
  * `posterior_sample_size`: How many draws from an MCMC chain were used for PSIS.
  * `data_size`: How many data points were used for PSIS.
