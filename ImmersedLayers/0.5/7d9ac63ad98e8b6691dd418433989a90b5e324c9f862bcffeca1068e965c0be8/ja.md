```
vecfield_from_scalarpotential!(v::Edges{Primal},ϕ::Nodes{Primal},base_cache::BasicILMCache)
```

スカラー電位場 `ϕ` に関連付けられたベクトル場 `v` を、勾配を介して返します。

$$
\mathbf{v} = \nabla\phi
$$
