```
vecfield_from_vectorpotential!(v::Edges{Primal},ψ::Nodes{Dual},base_cache::BasicILMCache)
```

Return the vector field `v` associated with vector potential field `ψ` (in 2-d, a scalar streamfunction), via the curl

$\mathbf{v} = \nabla\times\psi \mathbf{e}_z$
