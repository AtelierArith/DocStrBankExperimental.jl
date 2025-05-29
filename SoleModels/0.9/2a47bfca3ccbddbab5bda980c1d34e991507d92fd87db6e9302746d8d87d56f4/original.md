```
abstract type LeafModel{O} <: AbstractModel{O} end
```

Abstract type for leaf models, that is, models which outcomes do not depend other models, and represents the bottom of the computation.

In general, an [`AbstractModel`](@ref) can generally wrap other `AbstractModel`s; in such case, the outcome can depend on the inner models being applied on the instance object. Otherwise, the model is considered as a *leaf*, or *final*, and is the *leaf* of a tree of `AbstractModel`s.

# Examples

```julia-repl
julia> SoleModels.LeafModel(2) isa SoleModels.ConstantModel

julia> SoleModels.LeafModel(sum) isa SoleModels.FunctionModel
┌ Warning: Over efficiency concerns, please consider wrappingJulia Function's into FunctionWrapper{O,Tuple{SoleModels.AbstractInterpretation}} structures,where O is their return type.
└ @ SoleModels ~/.julia/dev/SoleModels/src/base.jl:337
true
```

See also [`AbstractModel`](@ref), [`ConstantModel`](@ref), [`FunctionModel`](@ref).
