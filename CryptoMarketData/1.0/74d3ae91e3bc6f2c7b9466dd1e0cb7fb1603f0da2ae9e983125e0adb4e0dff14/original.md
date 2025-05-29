```julia
get_saved_markets(; datadir)

```

Return a DataFrame that lists the currently saved markets.

# Keyword Arguments

  * datadir="./data" - directory where saved data is stored

# Example

```julia-repl
julia> saved = get_saved_markets()
10×4 DataFrame
 Row │ exchange       market          start       stop
     │ Any            Any             Any         Any
─────┼───────────────────────────────────────────────────────
   1 │ binance        BTCUSD_240628   2023-12-29  2024-02-17
   2 │ binance        BTCUSD_PERP     2020-08-11  2020-08-16
   3 │ bitget         BTCUSD_DMCBL    2019-04-23  2024-02-16
   4 │ bitget         DOGEUSD_DMCBL   2024-02-01  2024-02-20
   5 │ bitmex         ETHUSD          2018-08-02  2024-02-19
   6 │ bitstamp       BTCUSD          2011-08-18  2024-02-25
   7 │ bybit          ADAUSD          2022-03-24  2022-04-21
   8 │ bybit-inverse  ADAUSD          2022-03-24  2022-04-20
   9 │ bybit-linear   10000LADYSUSDT  2023-05-11  2024-03-04
  10 │ pancakeswap    BTCUSD          2023-03-15  2024-03-04
```
