```
struct DecisionForest{O} <: AbstractModel{O}
    trees::Vector{<:DecisionTree}
    info::NamedTuple
end
```

A [`DecisionForest`](@ref) is a symbolic model that wraps an ensemble of [`DecisionTree`](@ref).

See also [`DecisionList`](@ref), [`DecisionTree`](@ref), [`MixedModel`](@ref).
