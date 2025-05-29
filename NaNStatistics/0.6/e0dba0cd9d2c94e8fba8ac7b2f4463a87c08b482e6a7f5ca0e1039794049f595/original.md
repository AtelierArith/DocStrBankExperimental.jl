```julia
nanmad(A; dims)
```

Median absolute deviation from the median, ignoring `NaN`s, of an indexable collection `A`, optionally along a dimension specified by `dims`. Note that for a Normal distribution, sigma = 1.4826 * MAD.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
