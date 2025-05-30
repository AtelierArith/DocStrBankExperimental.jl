```
simplify(N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions}, allow_self_interactions::Bool=true)
```

相互作用を持つ種のみを含むネットワークの*コピー*を返します。内部的には、[`isdisconnected`](@ref)を呼び出します - `allow_self_interactions`の結果についてはこのドキュメントを参照してください。
