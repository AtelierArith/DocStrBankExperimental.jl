```julia
nanmean(A, W; dims)
```

Ignoring `NaN`s, calculate the weighted mean of an indexable collection `A`, optionally along dimensions specified by `dims`.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
