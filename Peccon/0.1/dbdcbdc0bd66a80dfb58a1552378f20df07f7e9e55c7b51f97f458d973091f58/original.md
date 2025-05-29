```
per_return(returns)
```

calculates the compounded return for a specific time-period from daily log returns 

```
# Examples
```

```julia-repl
julia> tickers = ["ADAEUR", "SPY"]
julia> data = fin_data(tickers)
julia> calc_returns(data, tickers)
julia> data_alpha(["ADAEUR", "SPY"])
```
