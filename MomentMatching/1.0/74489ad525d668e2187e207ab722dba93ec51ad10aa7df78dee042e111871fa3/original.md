```julia
load_on_procs(mode::MomentMatching.EstimationMode)

```

Loads model-specific files on all processes. Used only with multiprocessing. Should be defined for any subtype of [`EstimationMode`](@ref).
