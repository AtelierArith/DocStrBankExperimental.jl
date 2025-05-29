```
NeXLUncertainties.asa(::Type{DataFrame}, ffrs::AbstractVector{<:FitResult}; charOnly = true, withUnc = false, format = :normal # :pivot or :long)
```

Return generic `FitResult` as a DataFrame.

Format:

  * :normal - One row per spectrum, one column per k-ratio
  * :pivot - One row per ROI, one column per spectrum (optional: column for 1σ uncertainty on k-ratio)
  * :long - One row per spectrum, feature, measured k-ratio
