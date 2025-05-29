```
shrinkagenorm(m::MixedModel{T},
              θref::AbstractVector{T}=(isa(m, LinearMixedModel) ? 1e4 : 1) .*
                                      m.optsum.initial;
              uscale=false, p=2)
```

Returns a NamedTuple of Tables.jl-tables norm of the change from OLS estimates (across all relevant coefficients) to BLUPs from the mixed model.

`p` corresponds to the $L_p$ norms, i.e. $p=2$ is the Euclidean metric.

Each entry in the named tuple corresponds to a single grouping term.

!!! warning
    This function is **not** thread safe because it temporarily mutates the passed model before restoring its original form.

