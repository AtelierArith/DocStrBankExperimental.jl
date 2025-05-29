```julia
mergegloloc(
    estset::MomentMatching.EstimationSetup,
    resultglo::MomentMatching.EstimationResult,
    resultloc::MomentMatching.EstimationResult;
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult

```

Merges results from global and local estimations. Assumes inputs are ordered and uses aux, presh, pmm from local.
