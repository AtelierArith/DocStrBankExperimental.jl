A `Decision Forest` is a symbolic model that wraps an ensemble of models

```
struct DecisionForest{O} <: AbstractModel{O}
    trees::Vector{<:DecisionTree}
    info::NamedTuple
end
```

See also [`MixedModel`](@ref), [`DecisionList`](@ref), [`DecisionTree`](@ref).
