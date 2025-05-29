```
apply_bias_correction(
    ensemble::WeightedEnsembleNode,
    climate::Climate,
    obs::Vector{T};
    period=monthday
) where {T<:Real}
```

指定された期間（monthday）の中央値の誤差を使用してバイアス補正を適用します。
