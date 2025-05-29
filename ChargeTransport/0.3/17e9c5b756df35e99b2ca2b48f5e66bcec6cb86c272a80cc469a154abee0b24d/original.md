```julia
get_density(
    sol,
    ireg::Int64,
    ctsys,
    icc::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}
) -> Any

```

For given potentials, compute corresponding densities for given interior region corresponding to a homogeneous set of parameters.
