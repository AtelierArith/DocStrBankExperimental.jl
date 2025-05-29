```
masked_divv_from_divv_masked!(masked_divv::Nodes{Primal},divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

マスクされたベクトル場の発散 $\overline{\nabla\cdot\mathbf{v}}$ (`masked_divv`) を、マスクされたベクトル場の発散 $\nabla\cdot\overline{\mathbf{v}}$ (`divv`) から返します。これは以下の式から得られます。

$$
\overline{\nabla\cdot\mathbf{v}} = \nabla\cdot\overline{\mathbf{v}} - R_c\mathbf{n}\cdot[\mathbf{v}]
$$
