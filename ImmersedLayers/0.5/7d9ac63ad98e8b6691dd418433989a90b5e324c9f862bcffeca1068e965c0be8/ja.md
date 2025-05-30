```
vecfield_from_scalarpotential!(v::Edges{Primal},ϕ::Nodes{Primal},base_cache::BasicILMCache)
```

スカラー ポテンシャル フィールド `ϕ` に関連付けられたベクトル フィールド `v` を、勾配を介して返します。

$$
\mathbf{v} = \nabla\phi
$$
