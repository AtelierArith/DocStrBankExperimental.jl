```
AcbRefMatrix <: DenseMatrix{AcbRef}
```

Similar to [`AcbMatrix`](@ref) but indexing elements returns an `AcbRef` referencing the corresponding element instead of an `Acb` copy of the element. The constructors are the same as for `AcbMatrix
