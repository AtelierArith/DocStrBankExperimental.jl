```julia
tablemoms(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    glob,
    saving,
    filename_suffix
)

```

Compares model-generated moments with data in a table and optionally saves output.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).

# Optional arguments

  * saving: Logical, true if output has to be saved.
