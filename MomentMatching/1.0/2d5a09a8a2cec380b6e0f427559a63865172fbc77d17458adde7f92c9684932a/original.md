```julia
tablemoms(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    boot::MomentMatching.BootstrapResult;
    dgt,
    glob,
    saving,
    filename_suffix
)

```

Compares model-generated moments with data in a table and optionally saves output, bootstrap case.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).
  * boot: Instance of BootstrapResult. See separate documentation [`BootstrapResult`](@ref).

# Optional arguments

  * saving: Logical, true if output has to be saved.
