```
expand(mref::MeasureRef)::JuMP.AbstractJuMPScalar
```

Return a JuMP scalar function containing the explicit expansion of the measure `mref`. This expansion is done according to the measure data. Note that variables are added to the model as necessary to accomodate the expansion (i.e., point variables and semi-infinite variables are made as needed). Errors if expansion is undefined for the measure data and/or the measure expression. If desired this can be used in combination with [`measure`](@ref) to expand measures on the fly.

This is useful for extensions that employ a custom optimizer model since it can be used evaluate measures before expressions are translated to the new model. This method can also be extended to handle custom measure data types by extending [`expand_measure`](@ref). Optionally, [`analytic_expansion`](@ref) can also be extended which is triggered by [`is_analytic`](@ref) for such types if analytic expansion is possible in certain cases.

**Example**

```julia-repl
julia> tdata = DiscreteMeasureData(t, [0.5, 0.5], [0, 1])

julia> expr = expand(measure(g + z + T - h - 2, tdata))
0.5 g(0) + 0.5 g(1) + z + 0.5 T(0, x) + 0.5 T(1, x) - h(x) - 2
```
