```
cornu(
  x::AbstractMatrix{T},
  horizon::M,
  w::M;
  rho::T=0.2,
  init_budg=1,
  progress::Bool=false
) where {T<:AbstractFloat, M<:Integer}
```

Run CORN-U algorithm.

# Arguments

  * `x::AbstractMatrix{T}`: price relative matrix of assets.
  * `horizon::M`: The number of periods to invest.
  * `w::M`: maximum length of time window to be examined.

## Keyword Arguments

  * `rho::T=0.2`: The correlation coefficient threshold.
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

julia> model = cornu(x, 10, 5, 0.5);

julia> model.alg
"CORN-U"

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

See [`cornk`](@ref), and [`dricornk`](@ref).

# Reference

> [CORN: Correlation-driven nonparametric learning approach for portfolio selection](https://doi.org/10.1145/1961189.1961193)

