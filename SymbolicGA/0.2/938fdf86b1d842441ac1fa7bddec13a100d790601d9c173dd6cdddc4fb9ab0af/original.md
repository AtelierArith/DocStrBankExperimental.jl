```
Signature(positive::Int, negative::Int = 0, degenerate::Int = 0)
Signature(str::AbstractString) # Signature("++-𝟎")
```

Signature of an Euclidean or pseudo-Euclidean space.

This signature encodes a space with a metric such that the first `P` basis vectors square to 1, the following `N` to -1 and the following `D` to 0. The metric evaluates to zero between two distinct basis vectors.
