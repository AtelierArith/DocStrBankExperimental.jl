```
yahoo(symbol::AbstractString, opt::YahooOpt = YahooOpt())::TimeArray
yahoo(symbol::Symbol, opt::YahooOpt = YahooOpt())::TimeArray
```

This is a wrapper for downloading historical stock prices from Yahoo Finance.

The yahoo method takes a stock name in the form of a string and returns a `TimeSeries.TimeArray` corresponding to the Yahoo Finance ticker. With no argument, the default historical time series is the S&P 500.

# Examples

```julia
AAPL = yahoo(:AAPL)
SPX = yahoo("^GSPC")
NQ = yahoo("^IXIC")
```

```jl-repl
julia> start = DateTime(2018, 1, 1)
2018-01-01T00:00:00

julia> yahoo(:AAPL, YahooOpt(period1 = start))
655×6 TimeArray{Float64,2,Date,Array{Float64,2}} 2018-01-02 to 2020-08-07
...
```

# References

https://finance.yahoo.com

# See Also

  * fred()  which accesses the St. Louis Federal Reserve financial and economic data sets.
  * ons()   which is a wrapper to download financial and economic time series data from the Office for National Statistics (ONS).
