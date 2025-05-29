```
designmatrix(
    uf::UnfoldModel,
    tbl;
    eventcolumn = :event,
    contrasts = Dict{Symbol,Any}(),
    kwargs...,
```

`fit(UnfoldModel...)` から呼び出されるメイン関数で、デザインマトリックスを生成し、`<:AbstractDesignMatrix` のリストを返します。
