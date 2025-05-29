```
get_quantile_scores!{tp,N}(quantile_scores::AbstractArray{Float64, N}, scores::AbstractArray{tp,N}, quantiles::StepRangeLen{Float64} = 0.0:0.01:1.0)
```

return the quantiles of the given N dimensional `scores` array into a preallocated `quantile_scores` array, see `get_quantile_scores()`.
