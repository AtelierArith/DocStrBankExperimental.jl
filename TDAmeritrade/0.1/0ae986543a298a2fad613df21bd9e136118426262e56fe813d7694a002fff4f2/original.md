```
get_quotes(ticker)
get_quotes(ticker::Array)
```

Get quote of a symbol: https://developer.tdameritrade.com/quotes/apis/get/marketdata/{symbol}/quotes

`ticker` can be a single `String` or an `Array` or multiple `String`s

# Examples

```julia
get_quotes("GE")
get_quotes(["BA","GE"])
```
