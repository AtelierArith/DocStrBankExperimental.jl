```julia
estimation(
    estset::MomentMatching.EstimationSetup;
    npmm,
    cs,
    aux,
    presh,
    xlocstart,
    saving,
    saving_bestmodel,
    number_bestmodel,
    filename_suffix,
    errorcatching,
    vararg...
)

```

Estimate model parameters given instance of [`EstimationSetup`](@ref). 

Can be customized if non-default estimation cases have to be performed. Accepts initial guess(es) when only local stage is performed.
