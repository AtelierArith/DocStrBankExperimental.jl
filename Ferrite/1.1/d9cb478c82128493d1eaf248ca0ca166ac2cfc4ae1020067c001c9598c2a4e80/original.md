```
assemble!(A::AbstractAssembler, dofs::AbstractVector{Int}, Ke::AbstractMatrix)
assemble!(A::AbstractAssembler, dofs::AbstractVector{Int}, Ke::AbstractMatrix, fe::AbstractVector)
```

Assemble the element stiffness matrix `Ke` (and optional force vector `fe`) into the global stiffness (and force) in `A`, given the element degrees of freedom `dofs`.

This is equivalent to `K[dofs, dofs] += Ke` and `f[dofs] += fe`, where `K` is the global stiffness matrix and `f` the global force/residual vector, but more efficient.
