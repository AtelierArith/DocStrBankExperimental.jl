```
dricornk(
  x::AbstractMatrix{T},
  relpr_market::AbstractVector{T},
  horizon::M,
  k::M,
  w::M,
  p::M;
  lambda::T=1e-3,
  init_budg=1,
  progress::Bool=false
) where {T<:AbstractFloat, M<:Integer}
```

Run the DRICORNK algorithm.

# Arguments

  * `x::AbstractMatrix{T}`: A matrix of relative prices of the assets.
  * `relpr_market::AbstractVector{T}`: A vector of relative prices of the market in the same period.
  * `horizon::M`: The investment horizon.
  * `k::M`: The number of experts.
  * `w::M`: maximum length of time window to be examined.
  * `p::M`: maximum number of correlation coefficient thresholds.

## Keyword Arguments

  * `lambda::T=1e-3`: The regularization parameter.
  * `init_budg=1`: The initial budget for investment.
  * `progress::Bool=false`: Whether to show the progress bar.

!!! warning "Beware!"
    `x` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection

julia> stocks_ret, market_ret = rand(10, 100), rand(100);

julia> m_dricornk = dricornk(stocks_ret, market_ret, 5, 2, 4, 3);

julia> sum(m_dricornk.b, dims=1) .|> isapprox(1.) |> all
true
```

See [`cornk`](@ref), and [`cornu`](@ref).

# Reference

> [DRICORN-K: A Dynamic RIsk CORrelation-driven Non-parametric Algorithm for Online Portfolio Selection](https://www.doi.org/10.1007/978-3-030-66151-9_12)

