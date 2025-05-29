```
curlv_masked_from_masked_curlv!(curlv::Nodes{Dual},masked_curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

マスクされたベクトル場のカール $\nabla\times\overline{\mathbf{v}}$ (`curlv`) を、ベクトル場のマスクされたカール $\overline{\nabla\times\mathbf{v}}$ (`masked_curlv`) から返します。これは以下の式から得られます。

$$
\nabla\times\overline{\mathbf{v}} = \overline{\nabla\times\mathbf{v}} + R_n\mathbf{n}\times[\mathbf{v}]
$$
