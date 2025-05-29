```
calculate_profit(market::Market) -> NamedTuple{(:cleared_volumes, :clearing_prices, :profit), Tuple{Vector{Int}, Vector{Int}, Vector{Int}}}
```

市場から戦略的エージェントのクリアされたボリュームと価格を取得し、入札ごとの利益を計算します。
