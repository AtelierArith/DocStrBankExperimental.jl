```
render(::Type{Bipartite}, N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions})
```

ユニパーティットネットワークの二部投影を返します。構造上、種は二部ネットワークのレベル間で共有できないため、この操作は常に成功するとは限りません。失敗した場合は、[`BipartiteProjectionFailed`](@ref) 例外がスローされます。
