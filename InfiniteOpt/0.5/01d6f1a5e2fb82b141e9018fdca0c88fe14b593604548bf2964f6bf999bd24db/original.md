```
measure(expr::JuMP.AbstractJuMPScalar,
        data::AbstractMeasureData;
        [name::String = "measure"])::GeneralVariableRef
```

Return a measure reference that evaluates `expr` using according to `data`. The measure data `data` determines how the measure is to be evaluated. Typically, the `DiscreteMeasureData` and the `FunctionalDiscreteMeasureData` constructors can be used to for `data`. The variable expression `expr` can contain `InfiniteOpt` variables, infinite parameters, other measure references (meaning measures can be nested), and constants. Typically, this is called inside of `JuMP.@expression`, `JuMP.@objective`, and `JuMP.@constraint` in a manner similar  to `sum`. Note measures are not explicitly evaluated until  [`build_optimizer_model!`](@ref) is called or unless they are expanded via  [`expand`](@ref) or [`expand_all_measures!`](@ref).

**Example**

```julia-repl
julia> tdata = DiscreteMeasureData(t, [0.5, 0.5], [1, 2]);

julia> xdata = DiscreteMeasureData(xs, [0.5, 0.5], [[-1, -1], [1, 1]]);

julia> constr_RHS = @expression(model, measure(g - s + 2, tdata) + s^2)
measure{t}[g(t) - s + 2] + s²

julia> @objective(model, Min, measure(g - 1  + measure(T, xdata), tdata))
measure{xs}[g(t) - 1 + measure{xs}[T(t, x)]]
```
