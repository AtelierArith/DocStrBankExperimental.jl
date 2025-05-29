```
waeg(x::AbstractMatrix, ηₘᵢₙ::AbstractFloat, ηₘₐₓ::AbstractFloat, k::Integer)
```

Run Weak Aggregating Exponential Gradient (WAEG) algorithm.

# Arguments

  * `x::AbstractMatrix`: matrix of relative prices.
  * `ηₘᵢₙ::AbstractFloat`: minimum learning rate.
  * `ηₘₐₓ::AbstractFloat`: maximum learning rate.
  * `k::Integer`: number of EG experts.

# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

!!! warning "Beware!"
    `x` should be a matrix of size `n_assets` × `n_periods`.


# Example

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(4, 8);

julia> m = waeg(rel_pr, 0.01, 0.2, 20);

julia> m.b
4×8 Matrix{Float64}:
 0.25  0.238126  0.24158   0.2619    0.261729  0.27466   0.25148   0.256611
 0.25  0.261957  0.259588  0.248465  0.228691  0.24469   0.256674  0.246801
 0.25  0.245549  0.247592  0.254579  0.27397   0.259982  0.272341  0.290651
 0.25  0.254368  0.25124   0.235057  0.23561   0.220668  0.219505  0.205937

julia> sum(m.b, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [Boosting Exponential Gradient Strategy for Online Portfolio Selection: An Aggregating Experts’ Advice Method](https://doi.org/10.1007/s10614-019-09890-2)

