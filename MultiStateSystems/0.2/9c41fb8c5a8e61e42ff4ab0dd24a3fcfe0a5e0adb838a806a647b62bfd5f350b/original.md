```
add_user!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds a single user to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_source!(ntwᵖʷʳ, node = 1,
                           ind  = [:EENS])
```
