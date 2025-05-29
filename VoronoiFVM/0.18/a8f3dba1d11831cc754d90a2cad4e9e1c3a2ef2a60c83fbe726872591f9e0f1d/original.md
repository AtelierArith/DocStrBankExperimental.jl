```julia
struct DiscontinuousQuantity{Ti} <: VoronoiFVM.AbstractQuantity{Ti}
```

A discontinuous quantity is represented by different species in neigboring regions.

  * `regionspec::Vector`: Species numbers representing the quantity in each region

  * `id::Any`: Quantity identifier allowing to use the quantity as index in parameter fields
