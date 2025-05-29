```
designmatrix(
    uf::UnfoldModel,
    tbl;
    eventcolumn = :event,
    contrasts = Dict{Symbol,Any}(),
    kwargs...,
```

Main function called from `fit(UnfoldModel...)`, generates the designmatrix, returns a list of `<:AbstractDesignMatrix`
