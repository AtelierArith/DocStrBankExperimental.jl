```
isolated_system(atoms::AbstractVector; kwargs...)
```

Construct a [`FlexibleSystem`](@ref) by placing the passed `atoms` into an infinite vacuum (standard setup for modelling molecular systems). Extra `kwargs` are stored as custom system properties.

# Examples

Construct a hydrogen molecule

```julia-repl
julia> hydrogen = isolated_system([:H => [0, 0, 1.]u"bohr", :H => [0, 0, 3.]u"bohr"])
```
