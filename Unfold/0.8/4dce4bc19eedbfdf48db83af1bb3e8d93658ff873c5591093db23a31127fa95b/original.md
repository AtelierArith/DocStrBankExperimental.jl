```
designmatrix(
    T::Type{<:UnfoldModel},
    design_array::Vector{<:Pair},
    tbl;
    eventcolumn = :event,
    contrasts = Dict{Symbol,Any}(),
    kwargs...,
```

iteratively calls `designmatrix` for each event in the design_array, and returns a list of `<:AbstractDesignMatrix`
