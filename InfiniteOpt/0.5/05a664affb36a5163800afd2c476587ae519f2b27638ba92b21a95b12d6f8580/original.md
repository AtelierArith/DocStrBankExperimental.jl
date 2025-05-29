```
expand_measures(expr, write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

Expand all `MeasureRef`s in `expr` in-place via [`expand_measure`](@ref) and return the expanded expression. This is an internal method used by [`expand_all_measures!`](@ref) and `TranscriptionOpt` but can be useful for user-defined optimizer model extensions that add implement [`add_point_variable`](@ref)/[`add_semi_infinite_variable`](@ref) in combination  with `expand_measure`. `write_model` is the model that the measure variables are  added to as described in [`expand_measure`](@ref).
