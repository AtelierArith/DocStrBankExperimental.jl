```
pkimport(time, obs;
    kelauto = true,
    elimrange = ElimRange(),
    dosetime = DoseTime(),
    id = Dict{Symbol, Any}(),
    limitrule::Union{Nothing, LimitRule} = nothing,
    warn = true,
    kwargs...)
```

Import PK data from time vector `time` and concentration vector `obs`.
