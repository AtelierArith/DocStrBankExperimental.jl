```
vectorpotential_from_curlv!(ψ::Nodes{Dual},curlv::Nodes{Dual},base_cache::BasicILMCache)
```

Return the vector potential field `ψ` from the curl of the masked vector field, `curlv` ($\nabla\times\overline{\mathbf{v}}$), the jump in the vector field across immersed surface `dv`. It solves

$L_n\psi = -\nabla\times\overline{\mathbf{v}}$

and returns $\psi$.
