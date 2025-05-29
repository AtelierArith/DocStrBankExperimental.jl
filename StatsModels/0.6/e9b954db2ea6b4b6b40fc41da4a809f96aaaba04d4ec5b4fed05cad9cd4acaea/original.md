```
Term <: AbstractTerm
```

A placeholder for a variable in a formula where the type (and necessary data invariants) is not yet known.  This will be converted to a [`ContinuousTerm`](@ref) or [`CategoricalTerm`](@ref) by [`apply_schema`](@ref).

# Fields

  * `sym::Symbol`: The name of the data column this term refers to.
