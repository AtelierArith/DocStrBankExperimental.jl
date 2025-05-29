```
sort_vars(partable::ParameterTable)
sort_vars(partables::EnsembleParameterTable)
```

Sort variables in `partable` so that all independent variables are before the dependent variables, and return a copy of `partable` where the sorted variables are in `partable.sorted_vars`.

See [sort_vars!](@ref) for in-place version.
