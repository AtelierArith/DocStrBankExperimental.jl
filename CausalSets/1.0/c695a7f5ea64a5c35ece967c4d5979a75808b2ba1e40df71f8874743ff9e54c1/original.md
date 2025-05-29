```
cardinality_of(causet, i, j[, max_cardinality]) -> Union{Int64, Nothing}
```

Calculate the cardinality $Z(e_i, e_j)$. Return `nothing` if $e_i$ is not in the past of $e_j$.

If the parameter `max_cardinality` is specified, the function will return `nothing` if the cardinality exceeds `max_cardinality`. This is useful for optimization purposes.
