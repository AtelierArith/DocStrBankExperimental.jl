```
masked_curlv_from_curlv_masked!(masked_curlv::Nodes{Dual},curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

Return the masked curl of the vector field $\overline{\nabla\times\mathbf{v}}$ (`masked_curlv`) from the curl of the masked vector field $\nabla\times\overline{\mathbf{v}}$ (`curlv`). It obtains this from

$\overline{\nabla\times\mathbf{v}} = \nabla\times\overline{\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]$
