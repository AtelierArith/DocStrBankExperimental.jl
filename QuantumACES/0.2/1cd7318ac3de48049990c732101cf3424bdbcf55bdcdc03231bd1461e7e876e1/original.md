```
get_layer_times(layer_types::Vector{Symbol}, layer_time_dict::Dict{Symbol, Float64})
```

Returns the times taken to implement each layer in the circuit based on their types in `layer_types` and the times specified in `layer*time*dict, including the time for final measurement and reset.
