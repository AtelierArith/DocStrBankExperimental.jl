```
quantile(d::AbstractUncertainValueDataset, p, n::Int; kwargs...)
```

不確実な値からなるデータセットの要素ごとの分位数 `p` を計算します。各要素に対して `n` 回のサンプルの分位数を取得します。
