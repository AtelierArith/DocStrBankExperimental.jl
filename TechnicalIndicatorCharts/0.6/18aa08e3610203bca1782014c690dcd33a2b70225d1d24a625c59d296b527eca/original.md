# Summary

A Chart is a mutable struct that has:

  * a name (typically of the asset like "BTCUSD" or "AAPL")
  * a timeframe (which controls how much time each candle on the chart represents)
  * a DataFrame to hold OHLCV values and indicator values
  * a Vector of `OnlineTechnicalIndicator`s to display on the chart.
  * another Vector of display configuration for each indicator.

If you were to go to [TradingView](https://tradingview.com/) and look at a chart, imagine what kind of data structure would be required to represent it in memory. That's what the `Chart` struct aims to be.

# Fields

  * `name::AbstractString`
  * `tf::Dates.Period`
  * `indicators::AbstractVector{OnlineTechnicalIndicators.TechnicalIndicator}`
  * `visuals::AbstractVector`
  * `df::DataFrames.DataFrame`
  * `ts::Union{Missing, Dates.DateTime}`
  * `candle::Union{Missing, TechnicalIndicatorCharts.Candle}`

# Constructors

```julia
Chart(name, tf; indicators=[], visuals=[])
```

# Examples

```julia-repl
julia> just_candles = Chart("ETHUSD", Minute(1))

julia> golden_cross = Chart(
           "BTCUSD", Hour(4);
           indicators = [
               SMA{Float64}(;period=50),
               SMA{Float64}(;period=200)
           ],
           visuals = [
               Dict(
                   :label_name => "SMA 50",
                   :line_color => "#E072A4",
                   :line_width => 2
               ),
               Dict(
                   :label_name => "SMA 200",
                   :line_color => "#3D3B8E",
                   :line_width => 5
               )
           ]
       )

julia> default_visuals = Chart(
           "BNBUSDT", Hour(4);
           indicators = [BB{Float64}(), StochRSI{Float64}()],
           visuals    = [nothing,       nothing]  # To use defaults, pass in `nothing`.
       )
```
