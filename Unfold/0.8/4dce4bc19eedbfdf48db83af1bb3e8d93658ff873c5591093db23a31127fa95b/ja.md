```
designmatrix(
    T::Type{<:UnfoldModel},
    design_array::Vector{<:Pair},
    tbl;
    eventcolumn = :event,
    contrasts = Dict{Symbol,Any}(),
    kwargs...,
```

design_array内の各イベントに対して`designmatrix`を反復的に呼び出し、`<:AbstractDesignMatrix`のリストを返します。
