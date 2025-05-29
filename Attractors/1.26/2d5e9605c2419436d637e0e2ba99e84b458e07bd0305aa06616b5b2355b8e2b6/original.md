```
aggregate_attractor_fractions(
    fractions_cont, attractors_cont, featurizer, group_config [, info_extraction]
)
```

Aggregate the already-estimated curves of fractions of basins of attraction of similar attractors using the same pipeline used by [`GroupingConfig`](@ref). The most typical application of this function is to transform the output of a [`global_continuation`](@ref) with [`RecurrencesFindAndMatch`](@ref) so that similar attractors, even across parameter space, are grouped into one "attractor". Thus, the fractions of their basins are aggregated.

You could also use this function to aggregate attractors and their fractions even in a single parameter configuration, i.e., using the output of [`basins_fractions`](@ref).

This function is useful in cases where you want the accuracy and performance of [`AttractorsViaRecurrences`](@ref), but you also want the convenience of "grouping" similar attractrors like in [`AttractorsViaFeaturizing`](@ref) for presentation or analysis purposes. For example, a high dimensional model of competition dynamics across multispecies may have extreme multistability. After finding this multistability however, one may care about aggregating all attractors into two groups: where a given species is extinct or not. This is the example highlighted in our documentation, in [Extinction of a species in a multistable competition model](@ref).

## Input

1. `fractions_cont`: a vector of dictionaries mapping labels to basin fractions.
2. `attractors_cont`: a vector of dictionaries mapping labels to attractors. 1st and 2nd argument are exactly like the return values of [`global_continuation`](@ref) with [`RecurrencesFindAndMatch`](@ref) (or, they can be the return of [`basins_fractions`](@ref)).
3. `featurizer`: a 1-argument function to map an attractor into an appropriate feature to be grouped later. Features expected by [`GroupingConfig`](@ref) are `SVector`.
4. `group_config`: a subtype of [`GroupingConfig`](@ref).
5. `info_extraction`: a function accepting a vector of features and returning a description of the features. I.e., exactly as in [`FeaturizeGroupAcrossParameter`](@ref). The 5th argument is optional and defaults to the centroid of the features.

## Return

1. `aggregated_fractions`: same as `fractions_cont` but now contains the fractions of the aggregated attractors.
2. `aggregated_info`: dictionary mapping the new labels of `aggregated_fractions` to the extracted information using `info_extraction`.

## Clustering attractors directly

*(this is rather advanced)*

You may also use the DBSCAN clustering approach here to group attractors based on their state space distance (the [`set_distance`](@ref)) by making a distance matrix as expected by the DBSCAN implementation. For this, use `identity` as `featurizer`, and choose [`GroupViaClustering`](@ref) as the `group_config` with `clust_distance_metric = set_distance` and provide a numerical value for `optimal_radius_method` when initializing the [`GroupViaClustering`](@ref), and also, for the `info_extraction` argument, you now need to provide a function that expects a *vector of `StateSpaceSet`s* and outputs a descriptor. E.g., `info_extraction = vector -> mean(mean(x) for x in vector)`.
