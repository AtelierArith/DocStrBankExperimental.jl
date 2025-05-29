```
anticor(adj_close::Matrix{T}, window::Int) where {T<:Real}
```

Run the Anticor algorithm on `adj_close` with window sizes `window`.

!!! warning "Beware!"
    `adj_close` should be a matrix of size `n_assets` × `n_periods`.


# Arguments

  * `adj_close::Matrix{T}`: matrix of adjusted close prices
  * `window::Int`: size of the window

# Returns

  * `::OPSAlgorithm(n_assets, b, alg)`: An OPSAlgorithm object.

# Example

```julia
julia> using OnlinePortfolioSelection

julia> adj_close = [
       1. 2.
       4. 9.
       7. 8.
       10. 11.
       13. 7.
       8. 17.
       19. 20.
       22. 23.
       25. 8.
       2. 12.
       5. 12.
       5. 0.
       0. 2.
       1. 1.
       ];

julia> adj_close = permutedims(adj_close);

julia> m_anticor = anticor(adj_close, 3);

julia> m_anticor.b
2×14 Matrix{Float64}:
 0.5  0.5  0.5  0.5  …  0.0  0.0  0.0  1.0
 0.5  0.5  0.5  0.5     1.0  1.0  1.0  0.0

julia> sum(m_anticor.b, dims=1) .|> isapprox(1., atol=1e-8) |> all
true
```

# References

> [Can We Learn to Beat the Best Stock](https://www.doi.org/10.1613/jair.1336)

