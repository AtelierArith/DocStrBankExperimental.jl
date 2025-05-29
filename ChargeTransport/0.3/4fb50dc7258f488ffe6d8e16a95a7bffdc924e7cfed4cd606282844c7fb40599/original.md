```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.OhmicContactDirichlet}
)

```

Creates ohmic boundary conditions via Dirichlet BC for the electrostatic potential $\psi$

$\psi  = \psi_0 + U$,

where $\psi_0$ contains some given value and $U$ is an applied voltage.

$f[\psi] =  -q/\delta  \sum_\alpha{ z_\alpha  (n_\alpha - C_\alpha) },$

where $C_\alpha$ corresponds to some doping w.r.t. the species $\alpha$.

The boundary conditions for electrons and holes are dirichlet conditions, where

$\varphi_{\alpha} = U.$`
