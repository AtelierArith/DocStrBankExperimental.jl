```
splitobs(n::Int, [at = 0.7]) -> Tuple
```

Pre-compute the indices for two disjoint subsets and return them as a tuple of two ranges. The first range will span the first `at` fraction of possible indices, while the second range will cover the rest. These indices are applicable to any data container of size `n`.

```julia
julia> splitobs(100, at = 0.7)
# (1:70,71:100)
```
