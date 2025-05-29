```
centrality(N::SpeciesInteractionNetwork{<:Unipartite, <:Union{Binary, Probabilistic}})
```

最初の引数として型が指定されていない場合、centrality関数は[`ClosenessCentrality`](@ref)を使用します。
