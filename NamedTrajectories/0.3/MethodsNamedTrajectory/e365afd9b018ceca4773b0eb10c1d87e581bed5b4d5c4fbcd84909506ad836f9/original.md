```
get_component_names(traj::NamedTrajectory, comps::AbstractVector{<:Int})
```

Returns the name of the component with the given indices. If only one component is found, the name is returned as a single symbol. Else, the names are returned as a vector of symbols.

The filter requires that the components are a complete subset of the given indices, so that a partial match is excluded from the returned names.
