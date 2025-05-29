```
chain_cardinality_abundances(causet, ::Val{N}[, max_cardinality]) -> Array{Int64, N}
```

Count the abundances of all chain cardinalities in `causet`.

The indices in the returned array are shifted by one: For instance, for `N = 3`, the index `(i+1, j+1, k+1)` will contain the count of chains with chain cardinality $(i, j, k)$ in the causet. Thus, the resulting array will have `N` axes with a size of `length(causet) + 1` each.

If the parameter `max_cardinality` is specified, this function will only count chain cardinalities whose indiviual cardinalies are smaller or equal to `max_cardinality`. Therefore, the axes of the resulting array will only have a size of `max_cardinality` each in this case.
