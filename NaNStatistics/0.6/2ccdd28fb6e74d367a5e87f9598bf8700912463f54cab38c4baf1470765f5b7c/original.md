```julia
nanaad(A; dims)
```

Mean (average) absolute deviation from the mean, ignoring `NaN`s, of an indexable collection `A`, optionally along a dimension specified by `dims`. Note that for a Normal distribution, sigma = 1.253 * AAD.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
