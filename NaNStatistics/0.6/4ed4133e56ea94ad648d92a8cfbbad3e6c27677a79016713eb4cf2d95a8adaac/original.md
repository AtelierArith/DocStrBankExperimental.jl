```julia
nanmedian(A; dims)
```

Calculate the median, ignoring NaNs, of an indexable collection `A`, optionally along a dimension specified by `dims`.

Reduction over multiple `dims` is not officially supported, though does work (in generally suboptimal time) as long as the dimensions being reduced over are all contiguous.

Also supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).
