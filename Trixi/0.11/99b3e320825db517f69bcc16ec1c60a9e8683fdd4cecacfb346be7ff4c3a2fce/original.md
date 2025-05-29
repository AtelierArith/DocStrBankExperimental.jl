```
ViscousFormulationLocalDG(penalty_parameter)
```

The local DG (LDG) flux from "The Local Discontinuous Galerkin Method for Time-Dependent Convection-Diffusion Systems" by Cockburn and Shu (1998).

The parabolic "upwinding" vector is currently implemented for `TreeMesh`; for all other mesh types, the LDG solver is equivalent to [`ViscousFormulationBassiRebay1`](@ref) with an LDG-type penalization.

  * Cockburn and Shu (1998). The Local Discontinuous Galerkin Method for Time-Dependent Convection-Diffusion Systems [DOI: 10.1137/S0036142997316712](https://doi.org/10.1137/S0036142997316712)
