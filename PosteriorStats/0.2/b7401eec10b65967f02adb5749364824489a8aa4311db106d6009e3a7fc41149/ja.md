```
summarize(data::AbstractArray, stats_funs...; kwargs...) -> SummaryStats
```

`data`の各パラメータに対して`stats_funs`の要約統計量を計算します。サイズは`(draws, chains, params)`です。
