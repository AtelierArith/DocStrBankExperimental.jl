```
Swap
```

An objecct to keep track of a swap

# Arguments:

  * `existing::Union{Symbol, Nothing}`: The existing variable
  * `new::Union{Symbol, Nothing}`: The variable to replace the existing
  * `obj_value::Real`: The objective value for this swap
  * `success::Union{Bool, Nothing}`: Whether the swap was successful
  * `all_fixed::Union{Array{Symbol}, Nothing}`: All the variable in swapper.to_consider which were fixed
  * `termination_status::Union{String, TerminationStatusCode, Nothing}`: TerminationStatusCode
  * `solve_time::Union{Real, Nothing}`: Time to solve
  * `Swap(existing, new)`: A constructor for a Swap object
