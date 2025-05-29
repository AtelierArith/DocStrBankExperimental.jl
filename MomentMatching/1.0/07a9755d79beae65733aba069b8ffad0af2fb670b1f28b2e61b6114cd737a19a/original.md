```julia
PredrawnShocks(
    mode::MomentMatching.EstimationMode,
    modelname::String,
    typemom::String,
    aux::MomentMatching.AuxiliaryParameters
) -> MomentMatching.EmptyPredrawnShocks

```

Set up default PredrawnShocks object. Should be defined for specific estimation mode only if it is used.
