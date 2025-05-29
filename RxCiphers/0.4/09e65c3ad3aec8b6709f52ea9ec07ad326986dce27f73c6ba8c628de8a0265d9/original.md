```
normalise!(arr::Array{AbstractFloat} [, dims]) -> Array{AbstractFloat}
```

Divides by the sum of `arr` to make the new sum `1.`, if `dims` are given, `arr` is normalised only in those dims.
