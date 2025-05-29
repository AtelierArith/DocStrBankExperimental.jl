```
psislw(lw, [wcpp, wtrunc])
```

Compute the Pareto smoothed importance sampling (PSIS).

# Arguments

  * `lw::AbstractArray`: Array of size n x m containing m sets of n log weights. It is also possible to provide one dimensional array of length n.
  * `wcpp::Real`: Percentage of samples used for GPD fit estimate (default is 20).
  * `wtrunc::Float64`: Positive parameter for truncating very large weights to n^wtrunc. Providing False or 0 disables truncation. Default values is 3/4.

# Returns

  * `lw_out::AbstractArray`: Smoothed log weights
  * `kss::AbstractArray`: Pareto tail indices
