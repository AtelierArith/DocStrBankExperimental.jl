```
LatticeBoltzmannEquations2D(; Ma, Re, collision_op=collision_bgk,
                           c=1, L=1, rho0=1, u0=nothing, nu=nothing)
```

The Lattice-Boltzmann equations

$$
\partial_t u_\alpha + v_{\alpha,1} \partial_1 u_\alpha + v_{\alpha,2} \partial_2 u_\alpha = 0
$$

in two space dimensions for the D2Q9 scheme.

The characteristic Mach number and Reynolds numbers are specified as `Ma` and `Re`. By the default, the collision operator `collision_op` is set to the BGK model. `c`, `L`, and `rho0` specify the mean thermal molecular velocity, the characteristic length, and the reference density, respectively. They can usually be left to the default values. If desired, instead of the Mach number, one can set the macroscopic reference velocity `u0` directly (`Ma` needs to be set to `nothing` in this case). Likewise, instead of the Reynolds number one can specify the kinematic viscosity `nu` directly (in this case, `Re` needs to be set to `nothing`).

The nine discrete velocity directions of the D2Q9 scheme are sorted as follows [4]:

```
  6     2     5       y
    ┌───┼───┐         │
    │       │         │
  3 ┼   9   ┼ 1        ──── x
    │       │        ╱
    └───┼───┘       ╱
  7     4     8    z
```

Note that usually the velocities are numbered from `0` to `8`, where `0` corresponds to the zero velocity. Due to Julia using 1-based indexing, here we use indices from `1` to `9`, where `1` through `8` correspond to the velocity directions in [4] and `9` is the zero velocity.

The corresponding opposite directions are:

  * 1 ←→ 3
  * 2 ←→ 4
  * 3 ←→ 1
  * 4 ←→ 2
  * 5 ←→ 7
  * 6 ←→ 8
  * 7 ←→ 5
  * 8 ←→ 6
  * 9 ←→ 9

The main sources for the base implementation were

1. Misun Min, Taehun Lee, **A spectral-element discontinuous Galerkin lattice Boltzmann method for nearly incompressible flows**, Journal of Computational Physics 230(1), 2011 [doi:10.1016/j.jcp.2010.09.024](https://doi.org/10.1016/j.jcp.2010.09.024)
2. Karsten Golly, **Anwendung der Lattice-Boltzmann Discontinuous Galerkin Spectral Element Method (LB-DGSEM) auf laminare und turbulente nahezu inkompressible Strömungen im dreidimensionalen Raum**, Master Thesis, University of Cologne, 2018.
3. Dieter Hänel, **Molekulare Gasdynamik**, Springer-Verlag Berlin Heidelberg, 2004 [doi:10.1007/3-540-35047-0](https://doi.org/10.1007/3-540-35047-0)
4. Timm Krüger et al., **The Lattice Boltzmann Method**, Springer International Publishing, 2017 [doi:10.1007/978-3-319-44649-3](https://doi.org/10.1007/978-3-319-44649-3)
