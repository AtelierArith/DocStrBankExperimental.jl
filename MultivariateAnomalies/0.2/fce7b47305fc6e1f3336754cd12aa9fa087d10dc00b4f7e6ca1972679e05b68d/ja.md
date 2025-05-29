```
get_quantile_scores!{tp,N}(quantile_scores::AbstractArray{Float64, N}, scores::AbstractArray{tp,N}, quantiles::StepRangeLen{Float64} = 0.0:0.01:1.0)
```

与えられた N 次元の `scores` 配列の分位数を事前に割り当てられた `quantile_scores` 配列に返します。`get_quantile_scores()` を参照してください。
