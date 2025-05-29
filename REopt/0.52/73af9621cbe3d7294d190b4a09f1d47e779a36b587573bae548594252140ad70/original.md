```
get_steam_turbine_defaults_size_class(;avg_boiler_fuel_load_mmbtu_per_hour::Union{Float64, Nothing}=nothing,
                                size_class::Union{Int64, Nothing}=nothing)
```

Depending on the set of inputs, different sets of outputs are determine in addition to all SteamTurbine cost and performance parameter defaults:     1. Inputs: avg*boiler*fuel*load*mmbtu*per*hour        Outputs: size*class, st*size*based*on*avg*heating*load*kw     2. Inputs: sized*class        Outputs: (gets defaults directly from size*class)
