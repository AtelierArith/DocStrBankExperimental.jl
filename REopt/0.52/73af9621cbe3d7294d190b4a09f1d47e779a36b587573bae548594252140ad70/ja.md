```
get_steam_turbine_defaults_size_class(;avg_boiler_fuel_load_mmbtu_per_hour::Union{Float64, Nothing}=nothing,
                                size_class::Union{Int64, Nothing}=nothing)
```

入力のセットに応じて、すべてのSteamTurbineコストおよび性能パラメータのデフォルトに加えて、異なる出力セットが決定されます:     1. 入力: avg*boiler*fuel*load*mmbtu*per*hour        出力: size*class, st*size*based*on*avg*heating*load*kw     2. 入力: sized*class        出力: (size*classからデフォルトを直接取得)
