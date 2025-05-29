```
simplify(N::SpeciesInteractionNetwork{<:Bipartite, <:Interactions})
```

相互作用のある種のみを含むネットワークの*コピー*を返します。内部的には、[`isdisconnected`](@ref)が呼び出されます。
