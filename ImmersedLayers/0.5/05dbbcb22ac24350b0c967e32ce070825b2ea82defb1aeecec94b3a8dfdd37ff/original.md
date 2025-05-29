```
scalarpotential_from_divv!(ϕ::Nodes{Primal},divv::Nodes{Primal},base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

Return the scalar potential field `ϕ` from the divergence of the masked vector field, `divv` ($\nabla\cdot\overline{\mathbf{v}}$) the jump in the vector field across immersed surface `dv`. It solves

$L_c\phi = \nabla\cdot\overline{\mathbf{v}}$

and returns $\phi$.
