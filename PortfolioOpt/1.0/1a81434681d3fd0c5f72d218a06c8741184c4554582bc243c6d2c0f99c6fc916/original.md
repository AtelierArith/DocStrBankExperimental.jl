```
sequential_backtest_market(strategy_logic::Function, market_history::VolumeMarketHistory) -> Vector{Real}, Vector{Real}
```

Simple sequential backtest functionality for strategies that return an array of invested money per asset. Ideal for statefull strategies.

API:

```julia
wealth_strategy, returns_strategy = sequential_backtest_market(market_history; date_range=date_range) 
    do market, past_returns
    # ... Strategy definition ...
    return investment_decision
end
```

Arguments:

  * `strategy_logic::Function`: Function that represents the investment strategy.
  * `market_history::MarketHistory`: Market history.

Optional Keywork Arguments:

  * `date_range`: Dates to be simulated with corresponding entries in the market history.
