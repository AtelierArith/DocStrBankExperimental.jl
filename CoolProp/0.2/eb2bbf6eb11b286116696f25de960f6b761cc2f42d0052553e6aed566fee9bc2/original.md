```
AbstractState_update(handle::Clong, input_pair::Clong, value1::Real, value2::Real)
AbstractState_update(handle::Clong, input_pair::AbstractString, value1::Real, value2::Real)
```

Update the state of the AbstractState.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `input_pair::Clong`: The integer value for the input pair obtained from get*input*pair_index(param::AbstractString)
  * `input_pair::AbstractString`: The name of an input pair
  * `value1`: The first input value
  * `value2`: The second input value

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
