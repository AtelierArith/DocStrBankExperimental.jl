```
ArbRefVector <: DenseMatrix{ArbRef}
```

Similar to [`ArbVector`](@ref) but indexing elements returns an `ArbRef` referencing the corresponding element instead of an `Arb` copy of the element. The constructors are the same as for `ArbVector`
