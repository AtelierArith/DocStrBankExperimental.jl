```
predecessors(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T) where {T}
```

一部ネットワークにおける種の前駆体は、その種が非ゼロの相互作用を受けるすべての種のリストです。確率的ネットワークの場合、これは非ゼロの相互作用確率を持つすべての種を含みます。

もしその種に前駆体がない場合、このメソッドは種の空のリスト、具体的には `Set{T}()` を返します。
