```julia
struct InterfaceQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

An interface quantity is represented by exactly one species number

  * `ispec::Any`: Species number representing the quantity

  * `bregspec::Vector`: boundary regions, where interface quantity is defined

  * `id::Any`: Quantity identifier allowing to use the quantity as index in parameter fields
