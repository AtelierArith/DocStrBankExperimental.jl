```
AbstractState_set_binary_interaction_double(handle::Clong, i::Int, j::Int, parameter::AbstractString, value::Float64)
```

Set binary interraction parameter for different mixtures model e.g.: "linear", "Lorentz-Berthelot"

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `i`: indice of the first fluid of the binary pair
  * `j`: indice of the second fluid of the binary pair
  * `parameter`: string wit the name of the parameter, e.g.: "betaT", "gammaT", "betaV", "gammaV"
  * `value`: the value of the binary interaction parameter

# Example

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> AbstractState_set_binary_interaction_double(handle, 0, 1, "betaT", 0.987);
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> AbstractState_keyed_output(handle, t)
349.32634425309755
julia> AbstractState_free(handle);
```
