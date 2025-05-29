```
function rprt(
  rel_pr::AbstractMatrix{T},
  horizon::Integer,
  w::Integer=5,
  ϑ::T=0.8,
  𝜖::Integer=50,
  bₜ::Union{Nothing, AbstractVector}=nothing
) where T<:AbstractFloat
```

Run RPRT algorithm.

# Arguments

  * `rel_pr::AbstractMatrix{T}`: A `asset × samples` matrix of relative prices.
  * `horizon::Integer`: Investment period.
  * `w::Integer=5`: Window length.
  * `ϑ::T=0.8`: Mixing parameter.
  * `𝜖::Integer=50`: Expected profiting level.
  * `bₜ::Union{Nothing, AbstractVector}=nothing`: Initial portfolio. Default value would lead to a uniform portfolio.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(3, 6);
julia> horizon = 2
julia> window = 3
julia> v = 0.2
julia> eps = 10
julia> b = [0.5, 0.3, 0.2];

julia> m_rprt = rprt(rel_pr, horizon, window, v, eps, b);

julia> m_rprt.b
3×2 Matrix{Float64}:
 0.5  1.0
 0.3  0.0
 0.2  2.03615e-10

julia> sum(m_rprt.b, dims=1) .|> isapprox(1.) |> all
true
```

# Reference

> [Reweighted Price Relative Tracking System for Automatic Portfolio Optimization](https://ieeexplore.ieee.org/document/8411138/)

