```
addcounts!(r, x, levels::UnitRange{<:Integer}, [wv::AbstractWeights])
```

Add the number of occurrences in `x` of each value in `levels` to an existing array `r`. For each `xi ∈ x`, if `xi == levels[j]`, then we increment `r[j]`.

If a weighting vector `wv` is specified, the sum of weights is used rather than the raw counts.
