```
daily_returns(portfolio, Tickers)
```

calculates the daily log returns of each stock in a portfolio based on the close price of the day. 

# Examples

```julia-repl
julia> tickers = ["ADAEUR", "SPY"]
julia> data = fin_data(tickers)
julia> calc_returns(data, tickers)
```
