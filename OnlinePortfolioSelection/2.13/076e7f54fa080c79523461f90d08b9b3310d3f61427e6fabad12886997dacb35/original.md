```
cornk(
  x::AbstractMatrix{<:AbstractFloat},
  horizon::T,
  k::T,
  w::T,
  p::T;
  init_budg=1,
  progress::Bool=false
) where T<:Integer
```

Run CORN-K algorithm.

# Arguments

  * `x::AbstractMatrix{<:AbstractFloat}`: price relative matrix of assets.
  * `horizon::T`: The number of periods to invest.
  * `k::T`: The number of top experts to be selected.
  * `w::T`: maximum length of time window to be examined.
  * `p::T`: maximum number of correlation coefficient thresholds.

## Keyword Arguments

  * `init_budg=1`: The initial budget for investment.
  * `progress::Bool=false`: Whether to show the progress bar.

!!! warning "Beware!"
    `x` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> x = rand(5, 100);

julia> model = cornk(x, 10, 3, 5, 3);

julia> model.alg
"CORN-K"

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

See [`cornu`](@ref), and [`dricornk`](@ref).

# Reference

> [CORN: Correlation-driven nonparametric learning approach for portfolio selection](https://doi.org/10.1145/1961189.1961193)

