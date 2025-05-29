```
chain_cardinality_of(causet, chain[, max_cardinality]) -> Union{NTuple, Nothing}
```

Calculate the chain cardinality of `chain`. Return `nothing` if `chain` is not a chain or if the atoms in `chain` are not causally ordered.
