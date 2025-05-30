```
vectorpotential_from_masked_curlv!(ψ::Nodes{Dual},masked_curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

マスクされたベクトル場のカールからベクトルポテンシャル場 `ψ` を返します。`masked_curlv` ($\overline{\nabla\times\mathbf{v}}$) は、浸透した表面 `dv` を横切るベクトル場のジャンプです。これは次の方程式を解きます。

$$
L_n\psi = -\overline{\nabla\times\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]
$$

そして $\psi$ を返します。
