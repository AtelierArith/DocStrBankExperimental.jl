```
bs(adj_close::Matrix{T}; last_n::Int=0) where {T<:AbstractFloat}
```

Run the Best So Far algorithm on the given data.

# Arguments

  * `adj_close::Matrix{T}`: A matrix of adjusted closing prices of assets.

## Keyword Arguments

  * `last_n::Int`: The number of periods to look back for the performance of each asset. If `last_n` is 0, then the performance is calculated from the first period to the previous period.

!!! warning "Beware!"
    The `adj_close` matrix should be in the order of assets x periods.


# Returns

  * `::OPSAlgorithm(n_assets, b, alg)`: An instance of `OPSAlgorithm`.

# Example

```julia
julia> using OnlinePortfolioSelection

julia> adj_close = rand(5, 10);

julia> model = bs(adj_close, last_n=2);

julia> model.b
5×10 Matrix{Float64}:
 0.2  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0  0.0
 0.2  0.0  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.2  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.2  1.0  1.0  0.0  0.0  0.0  1.0  0.0  1.0  1.0
 0.2  0.0  0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [KERNEL-BASED SEMI-LOG-OPTIMAL EMPIRICAL PORTFOLIO SELECTION STRATEGIES](https://doi.org/10.1142/S0219024907004251)

