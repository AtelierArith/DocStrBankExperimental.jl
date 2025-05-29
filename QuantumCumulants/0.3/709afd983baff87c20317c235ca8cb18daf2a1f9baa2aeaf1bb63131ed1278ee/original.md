```
SingleSum <: QTerm
```

Defines a symbolic summation over a term, using one [`Index`](@ref) entity.

# Fields:

  * term: A multiplication of q-number terms. When the multiplication contains any [`IndexedOperator`](@ref) with the same index as the summation-index, a symbolic sum will be created.
  * sum_index: The index, for which the summation will go over.
  * non*equal*indices: (optional) A vector of indices, for which the summation-index can not be equal with.
