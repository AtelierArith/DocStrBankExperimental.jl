```
struct DecisionForest{O} <: AbstractModel{O}
    trees::Vector{<:DecisionTree}
    info::NamedTuple
end
```

[`DecisionForest`](@ref) は、[`DecisionTree`](@ref) のアンサンブルをラップする象徴的なモデルです。

他に [`DecisionList`](@ref)、[`DecisionTree`](@ref)、[`MixedModel`](@ref) も参照してください。
