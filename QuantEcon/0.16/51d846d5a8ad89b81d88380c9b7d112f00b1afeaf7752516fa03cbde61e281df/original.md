```
qnwdist(
    d::Distributions.ContinuousUnivariateDistribution, N::Int,
    q0::Real=0.001, qN::Real=0.999, method::Union{T,Type{T}}=Quantile
) where T
```

Construct `N` quadrature weights and nodes for distribution `d` from the quantile `q0` to the quantile `qN`. `method` can be one of:

  * `Even`: nodes will be evenly spaced between the quantiles
  * `Quantile`: nodes will be placed at evenly spaced quantile values

To construct the weights, consider splitting the nodes into cells centered at each node. Specifically, let notation `z_i` mean the `i`th node and let `z_{i-1/2}` be 1/2 between nodes `z_{i-1}` and `z_i`. Then, weights are determined as follows:

  * `weights[1] = cdf(d, z_{1+1/2})`
  * `weights[N] = 1 - cdf(d, z_{N-1/2})`
  * `weights[i] = cdf(d, z_{i+1/2}) - cdf(d, z_{i-1/2})` for all i in 2:N-1

In effect, this strategy assigns node `i` all the probability associated with a random variable occuring within the node `i`s cell.

The weights always sum to 1, so they can be used as a proper probability distribution. This means that `E[f(x) | x ~ d] ≈ dot(f.(nodes), weights)`.
