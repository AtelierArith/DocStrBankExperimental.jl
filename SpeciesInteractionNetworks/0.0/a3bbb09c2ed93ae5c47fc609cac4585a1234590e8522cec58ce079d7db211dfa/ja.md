```
isdegenerate(N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions}, allow_self_interactions::Bool=true)
```

一部の相互作用がない種を持つ場合、単一部ネットワークは退化しています。場合によっては、自己相互作用のみを持つ種がネットワークから切り離されていると考えることが有用です - これは、2番目の引数に `false` を使用することで実現できます（デフォルトは、自己相互作用のみを持つ種が残ることを*許可*することです）。
