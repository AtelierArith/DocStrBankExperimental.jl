```
get_samples(cs::AbstractVector{ConvertedSamples}; skipmissing=true)
```

Extract the `Onda.Samples` from a collection of [`ConvertedSamples`](@ref) output from [`edf_to_onda_samples`](@ref).

If `skipmissing=true` (the default), only successfully converted samples will be returned.  If `skipmissing=false`, then some elements may be `missing`.
