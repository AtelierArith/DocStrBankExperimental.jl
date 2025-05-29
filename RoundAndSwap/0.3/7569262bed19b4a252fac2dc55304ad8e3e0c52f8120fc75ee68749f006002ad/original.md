```
Swapper
```

An object to keep track of all the swaps

# Arguments:

  * `to_swap::Array{Swap}`: A list of swaps yet to be done
  * `consider_swapping::Array{Symbol}`: The variables to consider swapping
  * `completed_swaps::Union{Array{Array{Swap}}, Nothing}`: The completed swaps
  * `sense::OptimizationSense`: The optimisation sense, MAX or MIN
  * `max_swaps::Real`: The maximum number of swaps to complete
  * `number_of_swaps::Int`: The number of swaps completed
  * `Swapper(to_swap, to_swap_with, model; max_swaps)`: A constructor
