```
FluxLMARS(c)(u_ll, u_rr, orientation_or_normal_direction,
             equations::CompressibleEulerEquations3D)
```

Low Mach number approximate Riemann solver (LMARS) for atmospheric flows using an estimate `c` of the speed of sound.

References:

  * Xi Chen et al. (2013) A Control-Volume Model of the Compressible Euler Equations with a Vertical Lagrangian Coordinate [DOI: 10.1175/MWR-D-12-00129.1](https://doi.org/10.1175/mwr-d-12-00129.1)
