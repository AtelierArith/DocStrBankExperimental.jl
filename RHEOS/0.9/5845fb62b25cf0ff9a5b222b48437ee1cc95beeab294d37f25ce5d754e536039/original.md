```
indexweight(self::RheoTimeData; elperiods::Vector{K}, time_boundaries::Union{Nothing, Vector{T}} = nothing, includelast=true) where {K<:Integer,T<:Real}
```

This function returns array indices (i.e. an array of integers) which can be sent to the `modelfit`, `modelstepfit` or `modeldiffeqfit` functions to provide a weighted fitting whilst maintaining constant sample-rate.

Note that `time_boundaries` must have one more entry than `elperiods` so that all sections of weighting are fully defined by beginning and end points.

`indexweight` can underweight indices or overweight them. If `elperiods` in a given boundary is negative, every `abs(n)` index will be used, where `n` is the `elperiod` corresponding to a given boundary. If `n` is positive, then indicies will be duplicated `n` times such that they are given a higher weighting during the fitting procedure. If number of elements per period (`elperiods`) is `1` or `-1` it returns the original indicies for that boundary, whilst `0` is not accepted as a valid argument for `elperiods`.

The last element may or may not be included. By default the last element is forced to be included but this can be negated by providing the keyword argument `includelast=false`.
