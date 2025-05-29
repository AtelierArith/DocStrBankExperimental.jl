```
add_transition!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

Adds a single transitions to the state-transition diagram `std` and fills its corresponding `PropDict` with the named arguments `kwargs`. One obligatory named argument is `:states`, describing the tuple (fr,to) of the from- and to-state.

# Example

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["normal operation state","failed state"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
julia> add_transition!(stdᵍᵉⁿ, rate = 0.001u"1/hr",
                               states = (1,2))
```
