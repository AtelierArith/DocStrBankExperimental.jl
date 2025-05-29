`Decision Forest`は、モデルのアンサンブルをラップする象徴的なモデルです。

```
struct DecisionForest{O} <: AbstractModel{O}
    trees::Vector{<:DecisionTree}
    info::NamedTuple
end
```

他にも[`MixedModel`](@ref)、[`DecisionList`](@ref)、[`DecisionTree`](@ref)を参照してください。
