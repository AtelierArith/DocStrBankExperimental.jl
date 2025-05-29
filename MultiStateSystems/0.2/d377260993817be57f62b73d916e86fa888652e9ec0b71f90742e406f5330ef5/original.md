```
add_state!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

Adds a single state to the state-transition diagram `std` and fills its corresponding `PropDict` with the named arguments `kwargs`.

# Example

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_state!(stdᵍᵉⁿ, name  = "normal operation state",
                          power = 100u"MW",
                          init  = 1.0)
```
