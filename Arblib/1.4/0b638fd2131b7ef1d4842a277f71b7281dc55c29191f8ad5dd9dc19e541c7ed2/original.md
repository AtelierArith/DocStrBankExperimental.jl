```
ArbRefMatrix <: DenseMatrix{ArbRef}
```

Similar to [`ArbMatrix`](@ref) but indexing elements returns an `ArbRef` referencing the corresponding element instead of an `Arb` copy of the element. The constructors are the same as for `ArbMatrix`
