```
AbstractState_get_fugacity(handle::Clong, i::Integer)
```

Return the fugacity of species `i`

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `i`: The index of the species

# Example

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> AbstractState_get_fugacity(handle, 0)
30227.119385400914
julia> AbstractState_free(handle);
```
