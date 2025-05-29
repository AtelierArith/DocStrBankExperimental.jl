```
subgraph(N::SpeciesInteractionNetwork{<:Bipartite{T}, <:Interactions}, top::Vector{T}, bottom::Vector{T}) where {T}
```

二部ネットワークからサブグラフを誘導するには、含めるノードのために二つの配列を指定します。どちらかの配列は `:` にすることもでき、その場合はネットワークのこの側の全ノードが使用されます。
