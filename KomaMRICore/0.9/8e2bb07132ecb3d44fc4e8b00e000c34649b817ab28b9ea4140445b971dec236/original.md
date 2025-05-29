```
mag = simulate_slice_profile(seq; z, sim_params)
```

Returns magnetization of spins distributed along `z` after running the Sequence struct.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `z`: (`=range(-2e-2,2e-2,200)`) range for the z axis
  * `sim_params`: (`::Dict{String, Any}`, `=Dict{String,Any}("Δt_rf"=>1e-6)`) dictionary with   simulation parameters

# Returns

  * `mag`: (`::SpinStateRepresentation`) final state of the magnetization vector
