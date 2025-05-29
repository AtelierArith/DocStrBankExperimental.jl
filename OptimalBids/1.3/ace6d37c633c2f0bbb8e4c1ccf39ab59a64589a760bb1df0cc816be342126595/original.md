```
profit_for_bid!(market::Market, new_bids::Vector{Any}) -> Float64
```

Calculates overall profit when market is cleared with `new_bids`. This function will sequentiall call `change_bids!`, `clear_market!` and calculate_profit.
