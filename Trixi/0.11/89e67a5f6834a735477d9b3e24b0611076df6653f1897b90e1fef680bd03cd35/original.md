```
min_max_speed_einfeldt(u_ll, u_rr, normal_direction, equations::CompressibleEulerEquations2D)
```

Computes the HLLE (Harten-Lax-van Leer-Einfeldt) flux for the compressible Euler equations. Special estimates of the signal velocites and linearization of the Riemann problem developed by Einfeldt to ensure that the internal energy and density remain positive during the computation of the numerical flux.

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)
  * Bernd Einfeldt, Claus-Dieter Munz, Philip L. Roe and Björn Sjögreen (1991) On Godunov-type methods near low densities. [DOI: 10.1016/0021-9991(91)90211-3](https://doi.org/10.1016/0021-9991(91)90211-3)
