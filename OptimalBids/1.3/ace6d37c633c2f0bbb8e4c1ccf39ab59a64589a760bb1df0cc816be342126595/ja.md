```
profit_for_bid!(market::Market, new_bids::Vector{Any}) -> Float64
```

`new_bids`で市場がクリアされたときの全体の利益を計算します。この関数は、`change_bids!`、`clear_market!`を順次呼び出し、利益を計算します。
