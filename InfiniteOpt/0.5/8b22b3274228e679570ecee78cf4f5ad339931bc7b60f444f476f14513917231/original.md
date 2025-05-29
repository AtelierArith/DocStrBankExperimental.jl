```
JuMP.delete(model::InfiniteModel,
            prefs::AbstractArray{<:DependentParameterRef})::Nothing
```

Extend `JuMP.delete` to delete dependent infinite parameters and their dependencies. All variables, constraints, and measure functions that depend on `prefs` are updated to exclude them. Errors if the parameters are contained in an `AbstractMeasureData` datatype that is employed by a measure since the measure becomes invalid otherwise. Thus, measures that contain this dependency must be deleted first. Note that [`parameter_refs`](@ref parameter_refs(::AbstractMeasureData)) needs to be extended to allow deletion of parameters when custom `AbstractMeasureData` datatypes are used. Note that any dependent infinite variables will have their start values reset to the default via [`reset_start_value_function`](@ref).

**Example**

```julia-repl
julia> print(model)
Min measure(g(t, x)*t + x) + z
Subject to
 z ≥ 0.0
 g(t, x) + z ≥ 42.0, ∀ t ∈ [0, 6], x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]
 g(0.5, x) = 0, x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]

julia> delete(model, x)

julia> print(model)
Min measure(g(t)*t) + z
Subject to
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0
```
