```
AcbRefVector <: DenseMatrix{AcbRef}
```

Similar to [`AcbVector`](@ref) but indexing elements returns an `AcbRef` referencing the corresponding element instead of an `Acb` copy of the element. The constructors are the same as for `AcbVector`
