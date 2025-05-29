```
masked_curlv_from_curlv_masked!(masked_curlv::Nodes{Dual},curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

ベクトル場のマスクされたカール $\overline{\nabla\times\mathbf{v}}$ (`masked_curlv`) を、マスクされたベクトル場のカール $\nabla\times\overline{\mathbf{v}}$ (`curlv`) から返します。これは以下の式から得られます。

$$
\overline{\nabla\times\mathbf{v}} = \nabla\times\overline{\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]
$$
