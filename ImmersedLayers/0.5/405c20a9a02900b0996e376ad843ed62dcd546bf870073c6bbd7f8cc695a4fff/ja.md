```
vecfield_from_vectorpotential!(v::Edges{Primal},ψ::Nodes{Dual},base_cache::BasicILMCache)
```

ベクトルポテンシャル場 `ψ` に関連付けられたベクトル場 `v` を、カールを介して返します

$$
\mathbf{v} = \nabla\times\psi \mathbf{e}_z
$$
