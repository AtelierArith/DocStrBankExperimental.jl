```
LjungBoxTest(data::Vector{T}, vars::Vector{T}, lag::Integer=1)
```

Ljung-Box `Q` 統計量を計算して、実現値のベクトル（`data`）とバリュー・アット・リスク予測（`vars`）によって示される違反/ヒットシーケンスの独立性に関する帰無仮説をテストします。`lag` は `Q` の構築に使用されるラグの数を指定します。
