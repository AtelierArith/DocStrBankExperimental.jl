```julia
tableest(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    glob,
    saving,
    filename_suffix
)

```

Creates DataFrame with parameter estimates and optionally saves it.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).

# Optional arguments

  * glob: Logical, true if only global stage was performed.
  * saving: Logical, true if output has to be saved.
