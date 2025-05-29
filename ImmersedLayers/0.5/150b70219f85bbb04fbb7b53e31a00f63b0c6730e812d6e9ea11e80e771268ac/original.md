```
masked_divv_from_divv_masked!(masked_divv::Nodes{Primal},divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

Return the masked divergence of the vector field $\overline{\nabla\cdot\mathbf{v}}$ (`masked_divv`) from the divergence of the masked vector field $\nabla\cdot\overline{\mathbf{v}}$ (`divv`). It obtains this from

$\overline{\nabla\cdot\mathbf{v}} = \nabla\cdot\overline{\mathbf{v}} - R_c\mathbf{n}\cdot[\mathbf{v}]$
