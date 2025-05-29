```
dmr(
  x::AbstractMatrix,
  horizon::Integer,
  α::Union{Nothing, AbstractVector{<:AbstractFloat}},
  n::Integer,
  w::Integer,
  η::AbstractFloat=0.
)
```

Run Distributed Mean Reversion (DMR) strategy.

# Arguments

  * `x::AbstractMatrix`: A matrix of asset price relatives.
  * `horizon::Integer`: Investment horizon.
  * `α::Union{Nothing, AbstractVector{<:AbstractFloat}}`: Vector of step sizes. If `nothing` is passed, the algorithm itself determines the values.
  * `w::Integer`: Window size.
  * `η::AbstractFloat=0.`: Threshold.

# Returns

  * `::OPSAlgorithm`: An object of type [`OPSAlgorithm`](@ref).

# Example

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> assets = [
         "MSFT", "META", "GOOG", "AAPL", "AMZN", "TSLA", "NVDA", "PYPL", "ADBE", "NFLX", "MMM", "ABT", "ABBV", "ABMD", "ACN", "ATVI", "ADSK", "ADP", "AZN", "AMGN", "AVGO", "BA"
       ]

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2021-01-01")["adjclose"] for ticker=assets]

julia> prices = stack(querry, dims=1)

julia> x = prices[:, 2:end]./prices[:, 1:end-1]

julia> eta = 0.

julia> alpha = nothing

julia> n = 10

julia> w = 4

julia> horizon = 50

julia> model = dmr(x, horizon, alpha, n, w, eta);

julia> model.b
22×50 Matrix{Float64}:
 0.0454545  0.0910112   0.0909008    …  0.0907232    0.090959     0.0909736
 0.0454545  0.00706777  0.00706777      0.00706777   0.00706777   0.0978817
 0.0454545  0.0954079   0.095159        0.00432265   0.00432265   0.0955929
 0.0454545  0.0964977   0.0962938       0.0960025    0.0967765    0.0966751
 0.0454545  0.00476753  0.0957164       0.0956522    0.0957777    0.00476753
 0.0454545  0.00550015  0.00550015   …  0.00550015   0.00550015   0.00550015
 0.0454545  0.00426904  0.0952782       0.0949815    0.0945237    0.00426904
 0.0454545  0.00317911  0.00317911      0.00317911   0.00317911   0.00317911
 0.0454545  0.0944016   0.00350562      0.00350562   0.0938131    0.00350562
 0.0454545  0.00150397  0.00150397      0.0921901    0.0918479    0.0912083
 0.0454545  0.0956671   0.0959533    …  0.0960898    0.0962863    0.0960977
 0.0454545  0.00365637  0.0945089       0.00365637   0.00365637   0.00365637
 0.0454545  0.0909954   0.000375678     0.000375678  0.000375678  0.000375678
 0.0454545  0.00487068  0.00487068      0.0958842    0.00487068   0.0951817
 0.0454545  0.0970559   0.00595991      0.096872     0.0972911    0.0973644
 0.0454545  0.00523895  0.00523895   …  0.00523895   0.00523895   0.0963758
 0.0454545  0.00764483  0.00764483      0.00764483   0.00764483   0.00764483
 0.0454545  0.0971981   0.0971457       0.0974226    0.0975877    0.0973244
 0.0454545  0.00218155  0.0930112       0.0934464    0.00218155   0.00218155
 0.0454545  0.0914433   0.0915956       0.000654204  0.000654204  0.000654204
 0.0454545  0.0937513   0.00289981   …  0.00289981   0.0937545    0.00289981
 0.0454545  0.00669052  0.00669052      0.00669052   0.00669052   0.00669052
```

# Reference

> [Distributed mean reversion online portfolio strategy with stock network](https://doi.org/10.1016/j.ejor.2023.11.021)

