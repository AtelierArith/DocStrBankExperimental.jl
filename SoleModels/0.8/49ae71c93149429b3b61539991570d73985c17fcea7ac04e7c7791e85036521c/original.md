```
struct ConstantModel{O} <: LeafModel{O}
    outcome::O
    info::NamedTuple
end
```

The simplest type of model is the `ConstantModel`; it is a `LeafModel` that always outputs the same outcome.

# Examples

```julia-repl
julia> SoleModels.LeafModel(2) isa SoleModels.ConstantModel

julia> SoleModels.LeafModel(sum) isa SoleModels.FunctionModel
┌ Warning: Over efficiency concerns, please consider wrappingJulia Function's into FunctionWrapper{O,Tuple{SoleModels.AbstractInterpretation}} structures,where O is their return type.
└ @ SoleModels ~/.julia/dev/SoleModels/src/base.jl:337
true

```

See also [`apply`](@ref), [`FunctionModel`](@ref), [`LeafModel`](@ref).
