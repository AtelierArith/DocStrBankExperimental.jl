```
get_timestep_generator_profiles(
    solution::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

Returns statistics about the generator profiles from the optimal dispatch `solution`:

  * `"Grid mix (kW)"`: how much power is from the substation
  * `"Solar DG (kW)"`: how much power is from Solar PV DER
  * `"Energy storage (kW)`: how much power is from Energy storage DER
  * `"Diesel DG (kW)"`: how much power is from traditional generator DER
