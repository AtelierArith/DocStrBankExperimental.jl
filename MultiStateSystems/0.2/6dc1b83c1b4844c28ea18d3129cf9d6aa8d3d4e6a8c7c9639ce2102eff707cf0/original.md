```
add_components!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds a single component to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_components!(ntwᵖʷʳ, edge = (1,2),
                               name = "cable 1",
                               std  = STD(power = [0u"MW",1500u"MW"],
                                          prob  = [0.2,0.8]))
```
