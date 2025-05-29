```julia
nanrange(A; dims)
```

Calculate the range (maximum - minimum) of an indexable collection `A`, ignoring `NaN`s, optionally along a dimension specified by `dims`.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
