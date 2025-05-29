```
vecfield_helmholtz!(v::Edges{Primal},curlv::Nodes{Dual},divv::Nodes{Primal},dv::VectorData,vp::Union{Edges{Primal},Nothing},base_cache::BasicILMCache,veccache::VectorFieldCache)
```

Recover the vector field `v` from the masked curl field `curlv` ($\overline{\nabla\times\mathbf{v}}$), divergence field `divv` ($\overline{\nabla\cdot\mathbf{v}}$), surface vector jump `dv` ($[\mathbf{v}]$), and additional irrotational, divergence-free vector field `vp`. It obtains this from the Helmholtz decomposition,

$\mathbf{v} = \nabla\times\psi + \nabla\phi + \mathbf{v}_p$

in which $\psi$ is the solution of

$L_n\overline{\psi} = -\overline{\nabla\times\mathbf{v}} - R_n\mathbf{n}\times[\mathbf{v}]$

in which $\phi$ is the solution of

$L_c\overline{\phi} = \overline{\nabla\cdot\mathbf{v}} + R_c\mathbf{n}\cdot[\mathbf{v}]$

It is important to stress that `curlv` is the masked curl of the vector field, not the curl of the masked vector field. To get this the former from the latter, use [`masked_curlv_from_curlv_masked!`](@ref). Similarly for `divv`, which is the masked divergence of the vector field, not the divergence of the masked vector field. One can use [`masked_divv_from_divv_masked!`](@ref) for this.

To specify the irrotational, divergence-free vector field `vp`, one can also simply provide a tuple, e.g., `(1.0,0.0)`, to specify a uniform vector field.
