```
ppt(
  prices::AbstractMatrix,
  w::Int,
  ϵ::Int,
  horizon::Int,
  b̂ₜ::AbstractVector=ones(size(prices, 1))/size(prices, 1)
)
```

Run the Price Peak Tracking (PPT) algorithm.

# Arguments

  * `prices::AbstractMatrix`: Matrix of prices.
  * `w::Int`: Window size.
  * `ϵ::Int`: Constraint parameter.
  * `horizon::Int`: Number of days to run the algorithm.
  * `b̂ₜ::AbstractVector=ones(size(prices, 1))/size(prices, 1)`: Initial weights.

!!! warning "Beware!"
    `prices` should be a matrix of size `n_assets` × `n_periods`.


# Output

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "AMZN", "GOOG", "MSFT"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2020-01-01")["adjclose"] for ticker in tickers];

julia> prices = stack(querry) |> permutedims;

julia> model = ppt(prices, 10, 100, 100);

julia> sum(model, dims=1) .|> isapprox(1.) |> all
true
```

# References

> [A Peak Price Tracking-Based Learning System for Portfolio Selection](https://doi.org/10.1109/TNNLS.2017.2705658)

