```
min_max_speed_einfeldt(u_ll, u_rr, orientation, equations::CompressibleEulerEquations1D)
```

Computes the HLLE (Harten-Lax-van Leer-Einfeldt) flux for the compressible Euler equations. Special estimates of the signal velocites and linearization of the Riemann problem developed by Einfeldt to ensure that the internal energy and density remain positive during the computation of the numerical flux.

Original publication:

  * Bernd Einfeldt (1988) On Godunov-type methods for gas dynamics. [DOI: 10.1137/0725021](https://doi.org/10.1137/0725021)

Compactly summarized:

  * Siddhartha Mishra, Ulrik Skre Fjordholm and Rémi Abgrall Numerical methods for conservation laws and related equations. [Link](https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra_hyperbolic_pdes.pdf)
