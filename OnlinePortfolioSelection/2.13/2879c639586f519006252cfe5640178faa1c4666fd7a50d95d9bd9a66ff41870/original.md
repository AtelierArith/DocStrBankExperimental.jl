```
eg(rel_pr::AbstractMatrix; eta::AbstractFloat=0.05)
```

Run Exponential Gradient (EG) algorithm.

# Arguments

  * `rel_pr::AbstractMatrix`: Historical relative prices.

## Keyword Arguments

  * `eta::AbstractFloat=0.05`: Learning rate.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> typeof(rel_pr), size(rel_pr)
(Matrix{Float64}, (3, 10))

julia> m_eg = eg(rel_pr);

julia> m_eg.b
3×10 Matrix{Float64}:
 0.333333  0.334092  0.325014  0.331234  0.314832  0.324674  0.326467  0.357498  0.353961  0.340167
 0.333333  0.345278  0.347718  0.337116  0.359324  0.363286  0.36466   0.348263  0.345386  0.355034
 0.333333  0.32063   0.327267  0.331649  0.325843  0.31204   0.308873  0.294239  0.300652  0.304799

julia> sum(m_eg.b, dims=1) .|> isapprox(1.0) |> all
true
```

# References

> [On-Line Portfolio Selection Using Multiplicative Updates](https://onlinelibrary.wiley.com/doi/10.1111/1467-9965.00058)

