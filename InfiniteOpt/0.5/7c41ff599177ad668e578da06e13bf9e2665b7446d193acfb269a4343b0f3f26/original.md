```
expand_all_measures!(model::InfiniteModel)::Nothing
```

Expand all of the measures used in the objective and/or constraints of `model`. The objective and constraints are updated accordingly. Note that variables are added to the model as necessary to accomodate the expansion (i.e., point variables and semi-infinite variables are made as needed). Errors if expansion is undefined for the measure data and/or the measure expression.

This is useful for extensions that employ a custom optimizer model since it can be used evaluate measures before `model` is translated into the new model. This method can also be extended to handle custom measure data types by extending [`expand_measure`](@ref). Note that this method leverages `expand_measure` via [`expand_measures`](@ref). Optionally, [`analytic_expansion`](@ref) can also be extended which is triggered by [`is_analytic`](@ref) for such types if analytic expansion is possible in certain cases.

**Example**

```julia-repl
julia> print(model)
Min integral{t ∈ [0, 6]}[g(t)*t] + z
Subject to
 T(t, x) ≥ 0.0, ∀ t ∈ [0, 6], xi ∈ [-1, 1]
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 integral{t ∈ [0, 6]}[T(t, x)] ≥ 0.0, ∀ x ∈ [-1, 1]

julia> expand_all_measures!(model)

julia> print(model)
Min 3 g(6) + z
Subject to
 T(t, x) ≥ 0.0, ∀ t ∈ [0, 6], xi ∈ [-1, 1]
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 0.5 T(0, x) + 0.5 T(6, xi) ≥ 0.0, ∀ x ∈ [-1, 1]
```
