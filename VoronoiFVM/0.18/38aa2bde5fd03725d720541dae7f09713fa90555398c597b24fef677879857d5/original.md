```julia
boundary_dirichlet!(system, ispec, ibc, v)

```

Set Dirichlet boundary condition for species ispec at boundary ibc:

$u_{ispec}=v$ on $\Gamma_{ibc}$

!!! info
    Starting with version 0.14, it is preferable to define boundary condtitions within the `bcondition` physics callback

