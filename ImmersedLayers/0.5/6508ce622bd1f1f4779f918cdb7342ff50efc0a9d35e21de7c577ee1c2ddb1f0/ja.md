```
scalarpotential_from_masked_divv!(ϕ::Nodes{Primal},masked_divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

マスクされたベクトル場の発散 `masked_divv` ($\overline{\nabla\cdot\mathbf{v}}$) からスカラー電位場 `ϕ` を返します。これは、浸漬面 `dv` を横切るベクトル場のジャンプを考慮します。次の方程式を解きます。

$$
L_c\phi = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]
$$

そして、$\phi$ を返します。
