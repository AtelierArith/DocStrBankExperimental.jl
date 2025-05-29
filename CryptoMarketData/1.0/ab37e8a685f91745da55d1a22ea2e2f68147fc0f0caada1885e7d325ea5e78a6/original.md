```julia
load(exchange, market; datadir, span, tf, table)

```

Load candles for the given exchange and market from the file system.

# Keyword Arguments

  * datadir="./data" - directory where saved data is stored
  * span - a `Date` span that defines what Dates to load candles.  If it's `missing`, load everything.
  * tf - a `Period` that is used to aggregate 1m candles into higher timeframes.
  * table - a Tables.jl-compatible struct to load candles into.  The default is `DataFrame`.

# Example

```julia-repl
julia> bitstamp = Bitstamp()
julia> btcusd4h = load(bitstamp, "BTC/USD"; span=Date("2024-01-01"):Date("2024-02-10"), tf=Hour(4))
```
