```
tppt(
  prices::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  ϵ::Integer=100,
  α::AbstractFloat=0.5
)
```

Run Trend Promote Price Tracking (TPPT) algorithm.

# Arguments

  * `prices::AbstractMatrix`: Prices of the assets. Each column is a period and each row is an asset.
  * `horizon::Integer`: The number of Investment periods.
  * `w::Integer`: The window size.
  * `ϵ::Integer`: Constraint parameter.
  * `α::AbstractFloat`: Exponential moving average parameter.

# Returns

  * `::OPSAlgorithm`: An [`OPSAlgorithm`](@ref) object.

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-12")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1);

julia> horizon, w = 3, 3;

julia> model = tppt(prices, horizon, w);

julia> model.b
3×3 Matrix{Float64}:
 0.333333  1.52594e-6  7.35766e-7
 0.333333  5.30452e-6  3.90444e-6
 0.333333  0.999993    0.999995
```

# References

> [An online portfolio strategy based on trend promote price tracing ensemble learning algorithm](https://doi.org/10.1016/j.knosys.2021.107957)

