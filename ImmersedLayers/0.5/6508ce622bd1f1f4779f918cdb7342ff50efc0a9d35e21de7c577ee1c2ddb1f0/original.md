```
scalarpotential_from_masked_divv!(ϕ::Nodes{Primal},masked_divv::Nodes{Primal},dv::VectorData,base_cache::BasicILMCache,dcache::ScalarPotentialCache)
```

Return the scalar potential field `ϕ` from the masked divergence of the vector field, `masked_divv` ($\overline{\nabla\cdot\mathbf{v}}$) the jump in the vector field across immersed surface `dv`. It solves

$L_c\phi = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]$

and returns $\phi$.
