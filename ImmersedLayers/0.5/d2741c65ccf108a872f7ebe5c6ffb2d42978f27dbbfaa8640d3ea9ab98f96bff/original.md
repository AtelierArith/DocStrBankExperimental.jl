```
curlv_masked_from_masked_curlv!(curlv::Nodes{Dual},masked_curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

Return the curl of the masked vector field $\nabla\times\overline{\mathbf{v}}$ (`curlv`) from the masked curl of the vector field $\overline{\nabla\times\mathbf{v}}$ (`masked_curlv`). It obtains this from

$\nabla\times\overline{\mathbf{v}} = \overline{\nabla\times\mathbf{v}} + R_n\mathbf{n}\times[\mathbf{v}]$
