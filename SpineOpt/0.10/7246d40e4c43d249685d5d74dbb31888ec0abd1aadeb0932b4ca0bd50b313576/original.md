```
active_stochastic_paths(
    m; stochastic_structure::Union{Object,Vector{Object}}, t::Union{TimeSlice,Vector{TimeSlice}}
)
```

An `Array` of stochastic paths, where each path is itself an `Array` of `stochastic_scenario` `Object`s.

The paths are obtained as follows.

1. Start with the stochastic DAG associated to model `m`.
2. Remove all the scenarios that are not in the given `stochastic_structure`.
3. Remove scenarios that don't overlap the given `t`.
4. Return all the paths from root to leaf in the remaining sub-DAG.
