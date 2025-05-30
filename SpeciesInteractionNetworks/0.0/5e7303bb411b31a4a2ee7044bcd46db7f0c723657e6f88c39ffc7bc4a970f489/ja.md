```
successors(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T) where {T}
```

一部ネットワークにおける種の後継者は、その種が非ゼロの相互作用を確立するすべての種のリストです。確率的ネットワークの場合、これは相互作用の非ゼロの確率を持つすべての種を含みます。

もしその種に後継者がいない場合、このメソッドは特に `Set{T}()` の空の種のリストを返します。
