```
struct ConstantModel{O} <: LeafModel{O}
    outcome::O
    info::NamedTuple
end
```

The simplest type of model is the `ConstantModel`; it is a [`LeafModel`](@ref) that always outputs the same outcome.

# Examples

```julia-repl
julia> cm = ConstantModel(2);
julia> outcome(cm)
2
```

See also [`apply`](@ref), [`LeafModel`](@ref).
