```
boundary_condition_slip_wall(u_inner, orientation, direction, x, t,
                             surface_flux_function, equations::CompressibleEulerEquations1D)
```

Determine the boundary numerical surface flux for a slip wall condition. Imposes a zero normal velocity at the wall. Density is taken from the internal solution state and pressure is computed as an exact solution of a 1D Riemann problem. Further details about this boundary state are available in the paper:

  * J. J. W. van der Vegt and H. van der Ven (2002) Slip flow boundary conditions in discontinuous Galerkin discretizations of the Euler equations of gas dynamics [PDF](https://reports.nlr.nl/bitstream/handle/10921/692/TP-2002-300.pdf?sequence=1)

    Should be used together with [`TreeMesh`](@ref).
