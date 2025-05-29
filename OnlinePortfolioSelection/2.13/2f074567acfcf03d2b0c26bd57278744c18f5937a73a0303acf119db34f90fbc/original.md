```
oldem(
  rel_pr::AbstractMatrix,
  horizon::S,
  w::S,
  L::S,
  s::S,
  σ::T,
  ξ::T,
  γ::T;
  bt::AbstractVector = ones(size(rel_pr, 1))/size(rel_pr, 1)
) where {S<:Integer, T<:AbstractFloat}
```

Run Online Low Dimension Ensemble Method (OLDEM).

# Arguments

  * `rel_pr::AbstractMatrix`: A matrix of size `n_assets` × `T` containing the price relatives of assets.
  * `horizon::S`: Investment horizon.
  * `w::S`: Window size.
  * `L::S`: Number of subsystems.
  * `s::S`: Number of assets in each subsystem.
  * `σ::T`: Kernel bandwidth.
  * `ξ::T`: tradeoff parameter.
  * `γ::T`: tradeoff parameter.

## Keyword Arguments

  * `bt::AbstractVector`: A vector of length `n_assets` containing the initial portfolio weights. Presumebly, the initial portfolio portfolio is the equally weighted portfolio. However, one can use any other portfolio weights that satisfy the following condition: $\sum_{i=1}^{n\_assets} b_{i} = 1$.
  * `progress::Bool=false`: Show the progress bar.

!!! warning "Beware!"
    `rel_pr` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["MSFT", "TSLA", "AAPL", "META", "MMM"];

julia> querry = [
         get_prices(ticker, startdt="2020-01-01", enddt="2020-01-15")["adjclose"]
         for ticker in tickers
       ];

julia> prices = stack(querry) |> permutedims;

julia> x = prices[:, 2:end]./prices[:, 1:end-1]
5×8 Matrix{Float64}:
 0.987548  1.00259  0.990882  1.01593  1.01249   0.995373  1.01202  0.992957
 1.02963   1.01925  1.0388    1.0492   0.978055  0.993373  1.09769  1.02488
 0.990278  1.00797  0.995297  1.01609  1.02124   1.00226   1.02136  0.986497
 0.994709  1.01883  1.00216   1.01014  1.01431   0.998901  1.01766  0.987157
 0.991389  1.00095  0.995969  1.01535  1.00316   0.995971  1.00249  1.00249

julia> σ = 0.025;
julia> w = 2;
julia> h = 4;
julia> L = 4;
julia> s = 3;

julia> model = oldem(x, h, w, L, s, σ, 0.002, 0.25);

julia> model.b
5×4 Matrix{Float64}:
 0.2  1.99964e-8  1.0         0.0
 0.2  1.0         0.0         0.0
 0.2  0.0         0.0         1.99964e-8
 0.2  0.0         0.0         1.0
 0.2  0.0         1.99964e-8  0.0
```

# References

> [Online portfolio selection with predictive instantaneous risk assessment](https://doi.org/10.1016/j.patcog.2023.109872)

