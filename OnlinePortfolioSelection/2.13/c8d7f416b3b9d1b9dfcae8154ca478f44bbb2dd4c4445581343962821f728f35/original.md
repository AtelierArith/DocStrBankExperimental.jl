```
aictr(
  prices::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  ϵ::Integer,
  σ::AbstractVector,
  trend_model::AbstractVector{<:TrendRep};
  bt::AbstractVector = ones(size(prices, 1))/size(prices, 1)
)
```

Run the Adaptive Input and Composite Trend Representation (AICTR) algorithm.

# Arguments

  * `prices::AbstractMatrix`: Matrix of prices.
  * `horizon::Integer`: Number investing days.
  * `w::Integer`: Window size.
  * `ϵ::Integer`: Update strength.
  * `σ::AbstractVector`: Vector of size `L` that contains the standard deviation of each trend representation.
  * `trend_model::AbstractVector{<:TrendRep}`: Vector of trend representations. [`SMAP`](@ref), [`EMA`](@ref), and [`PP`](@ref) are supported.

## Keyword Arguments

  * `bt::AbstractVector`: Initial portfolio vector of size `n_assets`.

!!! warning "Beware"
    `prices` should be a matrix of size `n_assets` × `n_periods`.


# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG", "AMZN", "META", "TSLA", "BRK-A", "NVDA", "JPM", "JNJ"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2019-12-31")["adjclose"] for ticker ∈ tickers];

julia> prices = stack(querry) |> permutedims;

julia> horizon = 5;

julia> w = 3;

julia> ϵ = 500;

julia> σ = [0.5, 0.5];

julia> models = [SMAP(), EMA(0.5)];

julia> bt = [0.3, 0.3, 0.4];

julia> model = aictr(prices, horizon, w, ϵ, σ, models)

julia> model.b
10×5 Matrix{Float64}:
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  1.0         6.92439e-8  0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         1.0         0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  6.92278e-8  0.0         0.0         0.0
 0.1  0.0         0.0         6.95036e-8  1.0
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         0.0         1.0         6.95537e-8
```

# References

> [Radial Basis Functions With Adaptive Input and Composite Trend Representation for Portfolio Selection](https://www.doi.org/10.1109/TNNLS.2018.2827952)

