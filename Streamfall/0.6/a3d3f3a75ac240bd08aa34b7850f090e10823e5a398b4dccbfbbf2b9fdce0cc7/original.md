```
apply_bias_correction(
    ensemble::WeightedEnsembleNode,
    climate::Climate,
    obs::Vector{T};
    period=monthday
) where {T<:Real}
```

Apply bias correction using the median error for a given period (monthday)
