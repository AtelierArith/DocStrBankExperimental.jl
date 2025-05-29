```
divv_masked_from_masked_divv!(divv::Nodes{Primal},masked_divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

マスクされたベクトル場の発散 $\nabla\cdot\overline{\mathbf{v}}$ (`divv`) を、ベクトル場のマスクされた発散 $\overline{\nabla\cdot\mathbf{v}}$ (`masked_divv`) から返します。これは以下の式から得られます。

$$
\nabla\cdot\overline{\mathbf{v}} = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]
$$
