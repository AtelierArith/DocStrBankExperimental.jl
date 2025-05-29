```
daily_returns(portfolio, Tickers)
```

は、日々の終値に基づいてポートフォリオ内の各株式のデイリー対数リターンを計算します。

# 例

```julia-repl
julia> tickers = ["ADAEUR", "SPY"]
julia> data = fin_data(tickers)
julia> calc_returns(data, tickers)
```
