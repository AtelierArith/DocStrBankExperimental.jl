```
calculate_profit(market::Market) -> NamedTuple{(:cleared_volumes, :clearing_prices, :profit), Tuple{Vector{Int}, Vector{Int}, Vector{Int}}}
```

Retrieves strategic agent's cleared volumes and prices from the market and calculates per bid profit.
