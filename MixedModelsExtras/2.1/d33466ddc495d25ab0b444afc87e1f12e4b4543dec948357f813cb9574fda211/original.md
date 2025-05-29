```
shrinkagetables(m::MixedModel{T},
                θref::AbstractVector{T}=(isa(m, LinearMixedModel) ? 1e4 : 1) .*
                                        m.optsum.initial;
                uscale=false) where {T}
```

Returns a NamedTuple of Tables.jl-tables of the change from OLS estimates to BLUPs from the mixed model.

Each entry in the named tuple corresponds to a single grouping term.

!!! warning
    This function is **not** thread safe because it temporarily mutates the passed model before restoring its original form.

