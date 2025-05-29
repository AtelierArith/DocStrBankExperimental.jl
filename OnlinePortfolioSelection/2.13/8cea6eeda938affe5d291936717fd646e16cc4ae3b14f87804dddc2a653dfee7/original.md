```
bk(rel_price::AbstractMatrix{T}, K::S, L::S, c::T) where {T<:AbstractFloat, S<:Integer}
```

Run Bᴷ algorithm.

# Arguments

  * `rel_price::AbstractMatrix{T}`: Relative prices of assets.
  * `K::S`: Number of experts.
  * `L::S`: Number of time windows.
  * `c::T`: The similarity threshold.

!!! warning "Beware!"
    `rel_price` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection

julia> daily_relative_prices = rand(3, 20);
julia> nexperts = 10;
julia> nwindows = 3;
julia> sim_thresh = 0.5;

julia> model = bk(daily_relative_prices, nexperts, nwindows, sim_thresh);

julia> model.b
3×20 Matrix{Float64}:
 0.333333  0.333333  0.354839  0.318677  …  0.333331  0.329797  0.322842  0.408401
 0.333333  0.333333  0.322581  0.362646     0.333339  0.340406  0.354317  0.295811
 0.333333  0.333333  0.322581  0.318677     0.333331  0.329797  0.322842  0.295789

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# Reference

> [NONPARAMETRIC KERNEL-BASED SEQUENTIAL INVESTMENT STRATEGIES](https://doi.org/10.1111/j.1467-9965.2006.00274.x)

