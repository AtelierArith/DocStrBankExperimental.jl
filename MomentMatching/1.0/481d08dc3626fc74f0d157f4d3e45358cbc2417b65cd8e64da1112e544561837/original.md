```julia
tableest(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    boot::MomentMatching.BootstrapResult;
    cilev,
    dgt,
    glob,
    saving,
    filename_suffix
)

```

Creates DataFrame with parameter estimates and optionally saves it, bootstrap case.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).
  * boot: Instance of BootstrapResult. See separate documentation [`BootstrapResult`](@ref).

# Optional arguments

  * cilev: Level of confidence intervals.
  * glob: Logical, true if only global stage was performed.
  * saving: Logical, true if output has to be saved.
