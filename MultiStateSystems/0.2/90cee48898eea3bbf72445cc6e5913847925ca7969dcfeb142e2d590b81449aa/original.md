```
add_transitions!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

Adds multiple transitions to the state-transition diagram `std` and fills their corresponding `PropDict` with the named arguments `kwargs`. Either an uniform argument is given which holds for all transitions or an array is given with the specific argument for each transition.

# Example

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["normal operation state","failed state"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
julia> add_transitions!(stdᵍᵉⁿ, rate = [0.001u"1/hr",0.01u"1/hr"],
                                states = [(1,2),(2,1)])
```

!!! note
    If the `:states` argument is not provided in the `add_transitions!` function, the from- and to-states will be determined based on the other arguments.


# Example (Alternative)

```julia-repl
julia> add_transitions!(stdᵍᵉⁿ, rate = [0.000u"1/hr" 0.010u"1/hr"
                                        0.001u"1/hr" 0.000u"1/hr"])
```
