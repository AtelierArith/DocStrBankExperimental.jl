```
modelmatrix(t::AbstractTerm, data; hints=Dict(), mod=StatisticalModel)
modelmatrix(mf::ModelFrame; data=mf.data)
```

Return the model matrix based on a term and a data source.  If the term `t` is a [`FormulaTerm`](@ref), this uses the right-hand side (predictor terms) of the formula; otherwise all columns are generated.  If a [`ModelFrame`](@ref) is provided instead of an `AbstractTerm`, the wrapped table is used as the data source by default.

Like [`response`](@ref), this will compute and apply a [`Schema`](@ref) before calling [`modelcols`](@ref) if necessary.  The optional `hints` and `mod` keyword arguments are passed to [`apply_schema`](@ref).

!!! note
    `modelmatrix` is provided as a convenience for interactive use.  For modeling packages that wish to support a formula-based interface, it is recommended to use the [`schema`](@ref) – [`apply_schema`](@ref) – [`modelcols`](@ref) pipeline directly

