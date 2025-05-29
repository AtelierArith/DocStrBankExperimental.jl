```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.OhmicContactRobin}
)

```

Creates ohmic boundary conditions via a penalty approach with penalty parameter $\delta$. For example, the right-hand side for the electrostatic potential $\psi$ is implemented as

$f[\psi]  = -q/\delta   ( (p - N_a) - (n - N_d) )$,

assuming a bipolar semiconductor. In general, we have for some given charge number $z_\alpha$

$f[\psi] =  -q/\delta  \sum_\alpha{ z_\alpha  (n_\alpha - C_\alpha) },$

where $C_\alpha$ corresponds to some doping w.r.t. the species $\alpha$.

The boundary conditions for electrons and holes are dirichlet conditions, where

$\varphi_{\alpha} = U$`

with $U$ as an applied voltage.
