```
FeaturizeGroupAcrossParameter <: GlobalContinuationAlgorithm
FeaturizeGroupAcrossParameter(mapper::AttractorsViaFeaturizing; kwargs...)
```

A method for [`global_continuation`](@ref). It uses the featurizing approach discussed in [`AttractorsViaFeaturizing`](@ref) and hence requires an instance of that mapper as an input. When used in [`global_continuation`](@ref), features are extracted and then grouped across a parameter range. Said differently, all features of all initial conditions across all parameter values are put into the same "pool" and then grouped as dictated by the `group_config` of the mapper. After the grouping is finished the feature label fractions are distributed to each parameter value they came from.

This continuation method is based on, but strongly generalizes, the approaches in the papers [Gelbrecht2020](@cite) and [Stender2021](@cite).

## Keyword arguments

  * `info_extraction::Function` a function that takes as an input a vector of feature-vectors (corresponding to a cluster) and returns a description of the cluster. By default, the centroid of the cluster is used. This is what the `attractors_cont` contains in the return of `global_continuation`.
