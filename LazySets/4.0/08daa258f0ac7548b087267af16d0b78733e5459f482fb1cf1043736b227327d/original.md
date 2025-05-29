```
σ(d::AbstractVector, cms::CachedMinkowskiSumArray)
```

Return a support vector of a cached Minkowski sum in a given direction.

### Input

  * `d`   – direction
  * `cms` – cached Minkowski sum

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the summand sets.

### Notes

The result is cached, i.e., any further query with the same direction runs in constant time. When sets are added to the cached Minkowski sum, the query is only performed for the new sets.
