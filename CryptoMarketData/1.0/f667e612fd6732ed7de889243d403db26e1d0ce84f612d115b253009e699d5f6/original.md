```julia
save!(exchange, market; datadir, startday, endday, delay)

```

Download 1m candles from the given exchange and market, and save them locally.

# Keyword Arguments

  * datadir="./data" - directory where saved data is stored
  * startday - a `Date` to start fetching candles from
  * endday - a `Date` to stop fetching candles
  * delay - a delay to be passed to `sleep()` that will pause between internal calls to `save_day!()`

# Example

```julia-repl
julia> bitstamp = Bitstamp()
julia> save!(bitstamp, "BTC/USD", endday=Date("2020-08-16"))
```
