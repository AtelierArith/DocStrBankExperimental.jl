```
indexed_complete(de::IndexedMeanfieldNoiseEquations)
```

From a set of differential equation of averages, find all averages that are missing and derive the corresponding equations of motion. Uses [`find_missing`](@ref) and [`indexed_meanfield`](@ref) to do so. Implementation for IndexedMeanfieldNoiseEquations.

# Optional arguments

*`order=de.order`: The order at which the [`cumulant_expansion`](@ref) is performed     on the newly derived equations. If `nothing`, the order is inferred from the     existing equations. *`filter_func=nothing`: Custom function that specifies whether some averages should     be ignored when completing a system. This works by calling `filter!(filter_func, missed)`     where `missed` is the vector resulting from [`find_missing`](@ref). Occurrences     of averages for which `filter_func` returns `false` are substituted to 0. *`extra_indices`: A Vector of symbols, representing extra [`Index`](@ref) entities, which are     needed and created in the process of finding missing terms. *`kwargs...`: Further keyword arguments are passed on to [`indexed_meanfield`](@ref) and     simplification.

see also: [`find_missing`](@ref), [`indexed_meanfield`](@ref), [`meanfield`](@ref), [`find_missing_sums`](@ref)
