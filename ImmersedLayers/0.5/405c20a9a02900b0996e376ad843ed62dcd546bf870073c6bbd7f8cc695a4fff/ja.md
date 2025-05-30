```
vecfield_from_vectorpotential!(v::Edges{Primal},ψ::Nodes{Dual},base_cache::BasicILMCache)
```

ベクトルポテンシャル場 `ψ` に関連するベクトル場 `v` を、カールを介して返します（2次元ではスカラー流れ関数）。

$$
\mathbf{v} = \nabla\times\psi \mathbf{e}_z
$$
