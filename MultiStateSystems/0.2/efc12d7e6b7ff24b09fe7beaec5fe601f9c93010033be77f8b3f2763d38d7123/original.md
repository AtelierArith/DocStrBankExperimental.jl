```
add_source!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds a single source to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> stdᵍᵉⁿ = solvedSTD(prob = [0.1,0.2,0.7],
                          flow = [0.0u"MW",0.5u"MW",2.0u"MW"])
julia> add_source!(ntwᵖʷʳ, node = 1,
                           name = "generator 1",
                           std  = stdᵍᵉⁿ)
```
