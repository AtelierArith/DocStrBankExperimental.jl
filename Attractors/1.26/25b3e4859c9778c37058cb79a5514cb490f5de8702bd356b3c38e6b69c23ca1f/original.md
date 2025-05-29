GroupingConfig

Supertype for configuration structs on how to group features together. Used in several occasions such as [`AttractorsViaFeaturizing`](@ref) or [`aggregate_attractor_fractions`](@ref).

Currently available grouping configurations are:

  * [`GroupViaClustering`](@ref)
  * [`GroupViaNearestFeature`](@ref)
  * [`GroupViaHistogram`](@ref)
  * [`GroupViaPairwiseComparison`](@ref)

## For developers

`GroupingConfig` defines an extendable interface. The only thing necessary for a new grouping configuration is to:

1. Make a new type and subtype `GroupingConfig`.
2. If the grouping allows for mapping individual features to group index, then instead extend the **internal function** `feature_to_group(feature, config)`. This will also allow doing `id = mapper(u0)` with [`AttractorsViaFeaturizing`](@ref).
3. Else, extend the function `group_features(features, config)`. You could still extend `group_features` even if (2.) is satisfied, if there are any performance benefits.
4. Include the new grouping file in the `grouping/all_grouping_configs.jl` and list it in this documentation string.
