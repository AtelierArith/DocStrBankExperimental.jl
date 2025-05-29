```
add_states!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

Adds multiple states to the state-transition diagram `std` and fills their corresponding `PropDict` with the named arguments `kwargs`. Either an uniform argument is given which holds for all states or an array is given with the specific argument for each state.

# Example

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["normal operation state","failed state"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
```
