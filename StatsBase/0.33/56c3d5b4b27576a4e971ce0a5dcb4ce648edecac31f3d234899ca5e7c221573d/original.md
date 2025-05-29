```
countmap(x; alg = :auto)
countmap(x::AbstractVector, wv::AbstractVector{<:Real})
```

Return a dictionary mapping each unique value in `x` to its number of occurrences.

If a weighting vector `wv` is specified, the sum of weights is used rather than the raw counts.

`alg` is only allowed for unweighted counting and can be one of:

  * `:auto` (default): if `StatsBase.radixsort_safe(eltype(x)) == true` then use                    `:radixsort`, otherwise use `:dict`.
  * `:radixsort`:      if `radixsort_safe(eltype(x)) == true` then use the                    [radix sort](https://en.wikipedia.org/wiki/Radix_sort)                    algorithm to sort the input vector which will generally lead to                    shorter running time. However the radix sort algorithm creates a                    copy of the input vector and hence uses more RAM. Choose `:dict`                    if the amount of available RAM is a limitation.
  * `:dict`:           use `Dict`-based method which is generally slower but uses less                    RAM and is safe for any data type.
