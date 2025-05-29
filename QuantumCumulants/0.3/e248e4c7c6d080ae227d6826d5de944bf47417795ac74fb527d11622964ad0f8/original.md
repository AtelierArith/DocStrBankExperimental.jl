```
IndexedAverageSum <: CNumber
```

Defines a symbolic summation over an average, or a multiplication of several averages, using one [`Index`](@ref) entity.

# Fields:

  * term: A multiplication of average terms.
  * sum_index: The index, for which the summation will go over.
  * non*equal*indices: (optional) A vector of indices, for which the summation-index can not be equal with.
