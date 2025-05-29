```
AbstractState_get_mole_fractions_satState(handle::Clong, saturated_state::AbstractString,
                                          fractions::Array{Float64})
```

Get the molar fractions for the AbstractState and the desired saturated State.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `saturated_state`: The string specifying the state (liquid or gas)
  * `fractions`: The array of fractions

# Example

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> gas_frac = [0.0, 0.0]
julia> AbstractState_get_mole_fractions_satState(handle, "gas", gas_frac)
julia> @show gas_frac
gas_frac = [0.30304421184833846, 0.6969557881516616]
julia> liq_frac = [0.0, 0.0]
julia> AbstractState_get_mole_fractions_satState(handle, "liquid", liq_frac)
julia> @show liq_frac
liq_frac = [0.4, 0.6]
julia> AbstractState_free(handle);
```
