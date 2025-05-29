```
sim_opt(returns, simulations= 5000, days=252)
```

simulates random portfolio combinations and calculates the expected return and standard deviation of the portfolio

# Examples

```julia-repl
julia> returns = daily_returns(data, tickers)
julia> sim_mpt(returns)
```
