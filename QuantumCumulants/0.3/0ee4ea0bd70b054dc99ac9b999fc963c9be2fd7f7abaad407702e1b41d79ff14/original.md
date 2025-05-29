```
complete(de::MeanfieldEquations)
```

From a set of differential equation of averages, find all averages that are missing and derive the corresponding equations of motion. Uses [`find_missing`](@ref) and [`meanfield`](@ref) to do so.

# Optional arguments

*`order=de.order`: The order at which the [`cumulant_expansion`](@ref) is performed     on the newly derived equations. If `nothing`, the order is inferred from the     existing equations. *`filter_func=nothing`: Custom function that specifies whether some averages should     be ignored when completing a system. This works by calling `filter!(filter_func, missed)`     where `missed` is the vector resulting from [`find_missing`](@ref). Occurrences     of averages for which `filter_func` returns `false` are substituted to 0. *`extra_indices=Vector`: Used for indexed equations. Can be used to specify additional     indices, that are needed for calculation. *`kwargs...`: Further keyword arguments are passed on to [`meanfield`](@ref) and     simplification.

see also: [`find_missing`](@ref), [`meanfield`](@ref)
