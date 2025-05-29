```
CountingAll <: AbstractProperty
CountingAll()
```

Counting the total number of sets exactly without overflow. e.g. for the [`IndependentSet`](@ref) problem, it counts the independent sets. Note that `PartitionFunction(0.0)` also does the counting. It is more efficient, but uses floating point numbers, which does not have arbitrary precision.

  * The corresponding tensor element type is `BigInt`.
  * The weights on graph does not have effect.
  * BLAS (GPU and CPU) and GPU are supported,
