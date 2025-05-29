```
get_chp_defaults_prime_mover_size_class(;hot_water_or_steam::Union{String, Nothing}=nothing,
                                    avg_boiler_fuel_load_mmbtu_per_hour::Union{Float64, Vector{Float64}, Nothing}=nothing,
                                    prime_mover::Union{String, Nothing}=nothing,
                                    size_class::Union{Int64, Nothing}=nothing,
                                    max_kw::Float64=NaN,
                                    boiler_efficiency::Union{Float64, Nothing}=nothing,
                                    avg_electric_load_kw::Union{Float64, Nothing}=nothing,
                                    max_electric_load_kw::Union{Float64, Nothing}=nothing,
                                    is_electric_only::Bool=false,
                                    thermal_efficiency::Float64=NaN)
```

Depending on the set of inputs, different sets of outputs are determine in addition to all CHP cost and performance parameter defaults:     1. Inputs: hot*water*or*steam and avg*boiler*fuel*load*mmbtu*per*hour        Outputs: prime*mover, size*class, chp*elec*size*heuristic*kw, chp*max*size*kw     2. Inputs: prime*mover and avg*boiler*fuel*load*mmbtu*per*hour        Outputs: size*class, chp*elec*size*heuristic*kw, chp*max*size*kw     3. Inputs: prime*mover and size*class        Outputs: (uses default hot*water*or*steam), chp*max*size*kw     4. Inputs: prime*mover        Outputs: default average size*class = 0, chp*max*size*kw     5. Inputs: prime*mover, avg*electric*load*kw, max*electric*load*kw        Outputs: chp*elec*size*heuristic*kw, chp*max*size*kw

The main purpose of this function is to communicate the following mapping of dependency of CHP defaults versus      hot*water*or*steam and avg*boiler*fuel*load*mmbtu*per*hour: If hot*water and <= 27 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = recip*engine of size*class X If hot*water and > 27 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = combustion*turbine of size*class X If steam and <= 7 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = recip*engine of size*class X If steam and > 7 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = combustion*turbine of size_class X

The threshold avg*boiler*fuel*load*mmbtu*per*hour are based on industry expert judgements for applicable prime_movers where reciprocating engine is more suitable for smaller sizes and hot water, and combustion turbine is more suitable for larger sizes and steam.

The determination of size_class and defaults based only on the electric load metrics is for non-heating "CHP", a.k.a. Prime Generator
