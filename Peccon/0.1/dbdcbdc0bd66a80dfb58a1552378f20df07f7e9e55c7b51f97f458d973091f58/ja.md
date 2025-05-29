```
per_return(returns)
```

は、日次対数リターンから特定の期間の複利リターンを計算します。

```
# 例
```

```julia-repl
julia> tickers = ["ADAEUR", "SPY"]
julia> data = fin_data(tickers)
julia> calc_returns(data, tickers)
julia> data_alpha(["ADAEUR", "SPY"])
```
