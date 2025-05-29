```julia
etaFunction(
    sol,
    ireg::Int64,
    ctsys,
    icc::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}
) -> Any

```

The argument of the statistics function for a given solution on a given interior region.
