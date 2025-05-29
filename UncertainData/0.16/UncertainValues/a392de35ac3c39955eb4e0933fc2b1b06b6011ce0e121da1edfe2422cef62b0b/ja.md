```
assigndist_normal(μ, lower, upper; nσ = 1,
    trunc_lower = -Inf, trunc_upper = Inf,
    tolerance = 1e-2μ)
```

位置パラメータ `μ` に基づいて、`lower` と `upper` の不確実性境界とともに正規分布にパラメータを割り当てます。`nσ` は、`lower` / `upper` が `μ` からどれだけ標準偏差離れているかを示します（それらは `μ` から等距離でなければなりません）。`trunc_lower` と `trunc_upper` は、指定された場合に分布を切り捨てます（デフォルトは `-Inf` と `Inf` です）。
