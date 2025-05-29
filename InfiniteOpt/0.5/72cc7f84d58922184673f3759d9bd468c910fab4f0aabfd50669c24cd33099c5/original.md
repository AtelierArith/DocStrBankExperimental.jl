```
JuMP.delete(model::InfiniteModel, pref::ScalarParameterRef)::Nothing
```

Extend `JuMP.delete` to delete scalar parameters and their dependencies. All variables, constraints, and measure functions that depend on `pref` are updated to exclude it. Errors if the parameter is used by an infinite variable or if it is contained in an  `AbstractMeasureData` DataType that is employed by a measure since the measure becomes invalid otherwise. Thus, measures that contain this dependency must be deleted first. Note that [`parameter_refs`](@ref parameter_refs(::AbstractMeasureData)) needs to be extended to allow deletion of parameters when custom `AbstractMeasureData` datatypes are used.

**Example**

```julia-repl
julia> delete(model, x)
```
