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

時間ベクトル `time` と濃度ベクトル `obs` からPKデータをインポートします。
