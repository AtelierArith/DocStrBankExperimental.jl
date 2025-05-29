```
psisloo(log_lik, [wcpp, wtrunc])
```

PSIS leave-one-out log predictive densities.

Computes the log predictive densities given posterior samples of the log likelihood terms p(y*i|	heta^s) in input parameter `log*lik`. Returns a sum of the leave-one-out log predictive densities`loo`, individual leave-one-out log predictive density terms`loos`and an estimate of Pareto tail indeces`ks`. If tail index k>0.5, variance of the raw estimate does not exist and if tail index k>1 the mean of the raw estimate does not exist and the PSIS estimate is likely to have large variation and some bias.

# Arguments

  * `log_lik::AbstractArray`: Array of size n x m containing n posterior samples of the log likelihood terms p(y_i|	heta^s).
  * `wcpp::Real`: Percentage of samples used for GPD fit estimate (default is 20).
  * `wtrunc::Float64`: Positive parameter for truncating very large weights to n^wtrunc. Providing False or 0 disables truncation. Default values is 3/4.

# Returns

  * `loo::Real`: sum of the leave-one-out log predictive densities.
  * `loos::AbstractArray`: Individual leave-one-out log predictive density terms.
  * `ks::AbstractArray`: Estimated Pareto tail indeces.
