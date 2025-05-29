```
optimize!(
    index::AbstractSearchIndex,
    kind::ErrorFunction=ParetoRecall(),
    space::AbstractSolutionSpace=optimization_space(index);
    kwargs...)
    optimize_index!(index, kind, space; kwargs...)
```

[`optimize_index!`](@ref) の特定のインデックス、種類、または空間に特化できるフロントエンド関数です。
