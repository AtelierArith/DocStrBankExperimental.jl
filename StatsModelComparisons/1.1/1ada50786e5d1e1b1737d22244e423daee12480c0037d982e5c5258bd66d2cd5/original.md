```
waic(ll::AbstractArray{<:Real}; pointwise=false, log_lik="log_lik, kwargs...)
```

Compute the Widely Applicable Information Criterion (WAIC).

# Arguments

  * `loglik::AbstractArray`   : A vector of posterior log likelihoods
  * `pointwise::Bool`         : Compute WAIC pointwise, return a vector

# Returns

  * `res::NamedTuple`: (WAIC=waics, lppd=lpd, penalty=pD, std_err=se) where

    WAIC                    : Sum of pointwise waic values (or pointwise vector)   lppd                    : Log pointwise predictive density   penalty                 : Penalty term ("overfitting penalty")   std_err                 : Standard error of pointwise waic values
