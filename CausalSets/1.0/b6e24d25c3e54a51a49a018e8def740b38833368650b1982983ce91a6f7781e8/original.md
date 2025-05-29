```
count_chains(causet, chain_length) -> Int64
```

Count the number of strictly ascending ordered chains with length `chain_length` atoms in `causet`. For `chain_length = 2`, this is equivalent to [`count_relations`](@ref).
