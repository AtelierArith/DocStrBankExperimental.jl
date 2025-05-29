```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.SchottkyBarrierLowering}
) -> Any

```

Creates Schottky boundary conditions with additional lowering which are modelled as

$\psi = - \phi_S/q  + \sqrt{ -\frac{ q  \nabla_{\boldsymbol{\nu}} \psi_\mathrm{R}}{4\pi \varepsilon_\mathrm{i}}} + U$,

where $\psi_\mathrm{R}$ denotes the electric potential with standard Schottky contacts and the same space charge density as $\psi$ and where $\varepsilon_\mathrm{i}}}$ corresponds to the image force dielectric constant.

To solve for this additional boundary conditions the projected gradient $\nabla_{\boldsymbol{\nu}} \psi_\mathrm{R}$ is stored within a boundary species and calculated in the method generic_operator!().
