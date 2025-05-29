```
vectorpotential_from_masked_curlv!(ψ::Nodes{Dual},masked_curlv::Nodes{Dual},dv::VectorData,base_cache::BasicILMCache,wcache::VectorPotentialCache)
```

Return the vector potential field `ψ` from the masked curl of the vector field, `masked_curlv` ($\overline{\nabla\times\mathbf{v}}$), the jump in the vector field across immersed surface `dv`. It solves

$L_n\psi = -\overline{\nabla\times\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]$

and returns $\psi$.
