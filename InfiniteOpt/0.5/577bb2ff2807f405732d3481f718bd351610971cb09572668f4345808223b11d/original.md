```
analytic_expansion(expr, data::AbstractMeasureData,
                   write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

Analytically, evaluate measure in the simple case where the measure expression `expr` doesn't depend on `data` and thus `expr` can be treated as a constant in conjunction with an analytic result of the `data`. This is intended as an internal method that is used by [`expand`](@ref) and [`expand_measures`](@ref). For unrecognized `data` types, `expand_measure` is called instead. User defined measure data type may choose to extend this method if desired. This is triggered when `is_analytic(mref) = true`.
