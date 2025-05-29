```
cardinality_abundances(causet[, max_cardinality]) -> Vector{Int64}
```

Count the abundances of all cardinalities in `causet`.

The indices in the resulting vector are shifted by one: The index `i+1` will contain the count of chains with cardinality $i$ in the causet. The resulting vector thus has length `length(causet) + 1`.

If `max_cardinality` is specified, this function will only count cardinalities up to `max_cardinality`. Then, the resulting vector will have a length of `max_cardinalities`.
