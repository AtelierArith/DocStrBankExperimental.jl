```
flux_shima_etal(u_ll, u_rr, orientation, equations::CompressibleEulerEquations1D)
```

This flux is is a modification of the original kinetic energy preserving two-point flux by

  * Yuichi Kuya, Kosuke Totani and Soshi Kawai (2018) Kinetic energy and entropy preserving schemes for compressible flows by split convective forms [DOI: 10.1016/j.jcp.2018.08.058](https://doi.org/10.1016/j.jcp.2018.08.058)

The modification is in the energy flux to guarantee pressure equilibrium and was developed by

  * Nao Shima, Yuichi Kuya, Yoshiharu Tamaki, Soshi Kawai (JCP 2020) Preventing spurious pressure oscillations in split convective form discretizations for compressible flows [DOI: 10.1016/j.jcp.2020.110060](https://doi.org/10.1016/j.jcp.2020.110060)
