```
recursive_eltype(x, unwrap_ad_types = Val(false))
```

Recursively determine the element type of a nested structure `x`. This is equivalent to doing `fmap(Lux.Utils.eltype, x)`, but this implementation uses type stable code for common cases.

For ambiguous inputs like `nothing` and `Val` types we return `Bool` as the eltype.

If `unwrap_ad_types` is set to `Val(true)` then for tracing and operator overloading based ADs (ForwardDiff, ReverseDiff, Tracker), this function will return the eltype of the unwrapped value.
