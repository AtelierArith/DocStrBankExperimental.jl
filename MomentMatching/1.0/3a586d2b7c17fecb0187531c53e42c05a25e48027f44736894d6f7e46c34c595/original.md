```julia
PreallocatedContainers(
    mode::MomentMatching.EstimationMode,
    modelname::String,
    typemom::String,
    aux::MomentMatching.AuxiliaryParameters
) -> MomentMatching.EmptyPreallocatedContainers

```

Set up default PreallocatedContainers object. Should be defined for specific estimation mode only if it is used.
