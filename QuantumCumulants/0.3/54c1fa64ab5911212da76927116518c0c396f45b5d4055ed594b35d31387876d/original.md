```
IndexedAverageDoubleSum <: CNumber
```

Defines a symbolic summation over an [`IndexedAverageSum`](@ref), using a [`Index`](@ref) entity. This schematically represent a double-sum over a multiplication of averages.

# Fields:

  * innerSum: An [`IndexedAverageSum`](@ref) entity.
  * sum_index: The index, for which the (outer) summation will go over.
  * non*equal*indices: (optional) A vector of indices, for which the (outer) summation-index can not be equal with.
