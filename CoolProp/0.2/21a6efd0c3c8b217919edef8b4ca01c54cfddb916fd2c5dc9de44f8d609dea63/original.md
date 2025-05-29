```
AbstractState_get_mole_fractions(handle::Clong, fractions::Array{Float64})
```

Get the molar fractions for the AbstractState.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `fractions`: The array of fractions

# Example

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> mole_frac = [0.0, 0.0]
julia> AbstractState_get_mole_fractions(handle, mole_frac)
julia> @show mole_frac
mole_frac = [0.4, 0.6]
julia> AbstractState_free(handle);
```
