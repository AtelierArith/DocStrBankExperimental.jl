```julia
struct ContinuousQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

A continuous quantity is represented by exactly one species number

  * `ispec::Any`: Species number representing the quantity

  * `id::Any`: Quantity identifier allowing to use the quantity as index in parameter fields
