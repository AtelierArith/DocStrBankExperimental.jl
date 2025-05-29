```
vectorpotential_from_curlv!(ψ::Nodes{Dual},curlv::Nodes{Dual},base_cache::BasicILMCache)
```

マスクされたベクトル場 `curlv` のカールからベクトルポテンシャル場 `ψ` を返します ($\nabla\times\overline{\mathbf{v}}$)、浸漬面 `dv` を横切るベクトル場のジャンプです。これは次の方程式を解きます。

$$
L_n\psi = -\nabla\times\overline{\mathbf{v}}
$$

そして $\psi$ を返します。
