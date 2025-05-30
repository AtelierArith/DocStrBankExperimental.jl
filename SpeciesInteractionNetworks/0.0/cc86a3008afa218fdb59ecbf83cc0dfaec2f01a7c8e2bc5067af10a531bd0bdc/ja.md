```
predecessors(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T) where {T}
```

一方ネットワークにおける種の前駆体は、その種が非ゼロの相互作用を受けるすべての種のリストです。確率的ネットワークの場合、これは非ゼロの相互作用確率を持つすべての種を含みます。

もしその種に前駆体が存在しない場合、このメソッドは特に `Set{T}()` の空の種のリストを返します。
