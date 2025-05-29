```julia
struct SymOperation{D} <: Crystalline.AbstractOperation{D}
```

  * `rotation::Crystalline.SquareStaticMatrices.SqSMatrix{D, Float64} where D`
  * `translation::StaticArraysCore.SVector{D, Float64} where D`
