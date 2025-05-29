```
expand_measure(expr, data::AbstractMeasureData,
               write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

Return the finite reformulation of a measure containing a variable/parameter expression `expr` with measure data `data`. Here `write_model` is the target model where this expanded expression will be used. Thus, any variables that need to be created will be added to `write_model`. The methods [`make_point_variable_ref`](@ref) and [`make_semi_infinite_variable_ref`](@ref) should be used as appropriate to create these variables. Note this is intended as an internal function, but will need to be extended for unsupported `expr` types and for user-defined measure data types. Principally, this is leveraged to enable the user methods [`expand`](@ref) and [`expand_all_measures!`](@ref).
