```
AbstractState_set_fractions(handle::Clong, fractions::Array{Float64})
```

Set the fractions (mole, mass, volume) for the AbstractState.

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
julia> AbstractState_keyed_output(handle, t)
352.3522212991724
julia> AbstractState_free(handle);
```
