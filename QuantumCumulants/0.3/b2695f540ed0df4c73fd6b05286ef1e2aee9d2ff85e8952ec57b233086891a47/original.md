```
DoubleSum <: QTerm
```

Defines a symbolic summation over another [`SingleSum`](@ref), using one [`Index`](@ref) entity. This corresponds to a double-summation over a multiplication of terms.

# Fields:

  * innerSum: A [`SingleSum`](@ref) entity.
  * sum_index: The index, for which the (outer) summation will go over.
  * NEI: (optional) A vector of indices, for which the (outer) summation-index can not be equal with.
