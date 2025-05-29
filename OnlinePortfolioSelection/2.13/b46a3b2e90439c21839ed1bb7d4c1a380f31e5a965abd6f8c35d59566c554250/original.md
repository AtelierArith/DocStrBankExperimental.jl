```
uniform(n_assets::Int, horizon::Int)
```

Construct uniform portfolios.

# Arguments

  * `n_assets::Int`: The number of assets.
  * `horizon::Int`: The number of investment periods.

# Returns

  * `::OPSAlgorithm`: An object of [`OPSAlgorithm`](@ref) type.

# Example

```julia
julia> using OnlinePortfolioSelection

julia> model = uniform(3, 10)

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```
