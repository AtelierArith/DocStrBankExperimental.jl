```
bcrp(rel_pr::AbstractMatrix{T}) where T<:AbstractFloat
```

Run Best Constant Rebalanced Portfolio (BCRP) algorithm.

# Arguments

  * `rel_pr::AbstractMatrix{T}`: Relative price matrix.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object

# Example

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(3, 8);

julia> m_bcrp = bcrp(rel_pr);

julia> m_bcrp.b
3×8 Matrix{Float64}:
 8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9
 1.0         1.0         1.0         1.0         1.0         1.0         1.0         1.0
 0.0         0.0         0.0         0.0         0.0         0.0         0.0         0.0

julia> sum(m_bcrp.b, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [Universal Portfolios](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9965.1991.tb00002.x)

