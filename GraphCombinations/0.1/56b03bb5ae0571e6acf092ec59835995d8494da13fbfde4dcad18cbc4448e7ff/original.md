```
canonical_form(graph::GraphRep, internal_indices::UnitRange{Int})::GraphRep
```

Finds the canonical representation of a graph under permutations of internal vertices. The canonical form is the lexicographically smallest graph representation achievable through permutation of `internal_indices`.
