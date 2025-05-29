```
get_timestep_load_served(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

Returns Load statistics from an optimal dispatch `solution`, and compares to the base load (non-shedded) in `network`, giving statistics for

  * `"Feeder load (%)"`: How much load is the feeder supporting,
  * `"Microgrid load (%)"`: How much load is(are) the microgrid(s) supporting,
  * `"Bonus load via microgrid (%)"`: How much extra load is being supported.

## Note

Currently, because microgrids are not explicitly defined yet (see 'settings' file for initial implementation of microgrid tagging), `"Bonus load via microgrid (%)"` only indicates how much charging is being performed on Storage.
