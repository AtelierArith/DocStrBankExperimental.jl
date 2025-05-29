```julia
nanmaximum(A; dims)
```

As `maximum` but ignoring `NaN`s: Find the largest non-`NaN` value of an indexable collection `A`, optionally along a dimension specified by `dims`.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
