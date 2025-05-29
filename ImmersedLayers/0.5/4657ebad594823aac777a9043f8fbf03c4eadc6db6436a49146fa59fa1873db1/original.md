```
divv_masked_from_masked_divv!(divv::Nodes{Primal},masked_divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

Return the divergence of the masked vector field $\nabla\cdot\overline{\mathbf{v}}$ (`divv`) from the masked divergence of the vector field $\overline{\nabla\cdot\mathbf{v}}$ (`masked_divv`). It obtains this from

$\nabla\cdot\overline{\mathbf{v}} = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]$
