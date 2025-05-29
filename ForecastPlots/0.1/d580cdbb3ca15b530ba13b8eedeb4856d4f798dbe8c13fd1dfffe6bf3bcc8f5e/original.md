Package: ForecastPlots

```
candel(x, t, args...; colors = (:green, :red), kw...)
```

Plot a candlestick for stock prices

# Arguments

  * `x`: Matrix with four columns for Open, High, Low and Close values.
  * `t`: Vector with time units, it defaults to 1:size(x,1)
  * `args...`: `plot` arguments
  * `colors`: Tuple with the up and down color symbols, it defaults to (:green,:red)
  * `kw...`: `plot` keyword arguments

# Returns

Candle plot

# Examples

```julia-repl
using MarketData

x = yahoo(:INTC)
last_month_intc = values(x)[end-30:end,1:4]
candle(last_month_intc)
candle(last_month_intc,timestamp(x)[end-30:end])
candle(last_month_intc,timestamp(x)[end-30:end]; colors=(:white,:black), title = "INTC")
```
