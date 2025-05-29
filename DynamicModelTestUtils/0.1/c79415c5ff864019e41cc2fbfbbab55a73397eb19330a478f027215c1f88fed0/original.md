```
compare(
    new_sol::SciMLBase.AbstractTimeseriesSolution,
    reference::DataFrame,
    over::Vector{<:Union{Pair{<:Any, String}, Pair{<:Any, Pair{String, String}}}}
    cmp=DefaultComparison(); warn_observed=true)
```

Lower level version of `compare` that lets you specify the mapping from values in `new_sol` (specified as either variable => name or variable => (input*name, output*name) pairs) to the column names in `reference`. The tuple-result version lets you specify what the column names are when passed to the comparison method. Since the mapping is explicit this version does not take `to_name`, but it still does take `warn_observed`. See the implicit-comparison version of `compare` for more information.
