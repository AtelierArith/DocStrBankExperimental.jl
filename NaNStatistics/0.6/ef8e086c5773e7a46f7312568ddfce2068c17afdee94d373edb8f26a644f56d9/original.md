```julia
nanpctile(A, p; dims)
```

Find the `p`th percentile (where `0 <= p <= 100`) of an indexable collection `A`, ignoring NaNs, optionally along a dimension specified by `dims`.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

See also `nanpctile!` for a more efficient in-place variant.
