```
SpecialIndexedTerm <: QTerm
```

A multiplication of [`IndexedOperator`](@ref) entities, with special constraint on the index-values. For example σᵢ²² * σⱼ²² with the constraint i ≠ j

# Fields:

  * term: A multiplication of q-number terms.
  * indexMapping: A Vector of [`Index`](@ref) tuples, specifying the contraints for the term. Each Tuple is considered to one constraint. e.g: (i,j) -> i ≠ j
