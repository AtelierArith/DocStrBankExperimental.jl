```
sim_opt(returns, simulations= 5000, days=252)
```

ポートフォリオのランダムな組み合わせをシミュレートし、ポートフォリオの期待リターンと標準偏差を計算します。

# 例

```julia-repl
julia> returns = daily_returns(data, tickers)
julia> sim_mpt(returns)
```
