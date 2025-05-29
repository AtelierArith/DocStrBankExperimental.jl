```
LatticeBoltzmannEquations3D(; Ma, Re, collision_op=collision_bgk,
                           c=1, L=1, rho0=1, u0=nothing, nu=nothing)
```

The Lattice-Boltzmann equations

$$
\partial_t u_\alpha + v_{\alpha,1} \partial_1 u_\alpha + v_{\alpha,2} \partial_2 u_\alpha + v_{\alpha,3} \partial_3 u_\alpha = 0
$$

in three space dimensions for the D3Q27 scheme.

The characteristic Mach number and Reynolds numbers are specified as `Ma` and `Re`. By the default, the collision operator `collision_op` is set to the BGK model. `c`, `L`, and `rho0` specify the mean thermal molecular velocity, the characteristic length, and the reference density, respectively. They can usually be left to the default values. If desired, instead of the Mach number, one can set the macroscopic reference velocity `u0` directly (`Ma` needs to be set to `nothing` in this case). Likewise, instead of the Reynolds number one can specify the kinematic viscosity `nu` directly (in this case, `Re` needs to be set to `nothing`).

The twenty-seven discrete velocity directions of the D3Q27 scheme are sorted as follows [4]:

  * plane at `z = -1`:

    ```
      24    17     21       y
         ┌───┼───┐          │
         │       │          │
      10 ┼   6   ┼ 15        ──── x
         │       │         ╱
         └───┼───┘        ╱
      20    12     26    z
    ```
  * plane at `z = 0`:

    ```
      14     3     7        y
         ┌───┼───┐          │
         │       │          │
       2 ┼  27   ┼ 1         ──── x
         │       │         ╱
         └───┼───┘        ╱
       8     4     13    z
    ```
  * plane at `z = +1`:

    ```
      25    11     19       y
         ┌───┼───┐          │
         │       │          │
      16 ┼   5   ┼ 9         ──── x
         │       │         ╱
         └───┼───┘        ╱
      22    18     23    z
    ```

Note that usually the velocities are numbered from `0` to `26`, where `0` corresponds to the zero velocity. Due to Julia using 1-based indexing, here we use indices from `1` to `27`, where `1` through `26` correspond to the velocity directions in [4] and `27` is the zero velocity.

The corresponding opposite directions are:

  * 1 ←→  2
  * 2 ←→  1
  * 3 ←→  4
  * 4 ←→  3
  * 5 ←→  6
  * 6 ←→  5
  * 7 ←→  8
  * 8 ←→  7
  * 9 ←→ 10
  * 10 ←→  9
  * 11 ←→ 12
  * 12 ←→ 11
  * 13 ←→ 14
  * 14 ←→ 13
  * 15 ←→ 16
  * 16 ←→ 15
  * 17 ←→ 18
  * 18 ←→ 17
  * 19 ←→ 20
  * 20 ←→ 19
  * 21 ←→ 22
  * 22 ←→ 21
  * 23 ←→ 24
  * 24 ←→ 23
  * 25 ←→ 26
  * 26 ←→ 25
  * 27 ←→ 27

The main sources for the base implementation were

1. Misun Min, Taehun Lee, **A spectral-element discontinuous Galerkin lattice Boltzmann method for nearly incompressible flows**, Journal of Computational Physics 230(1), 2011 [doi:10.1016/j.jcp.2010.09.024](https://doi.org/10.1016/j.jcp.2010.09.024)
2. Karsten Golly, **Anwendung der Lattice-Boltzmann Discontinuous Galerkin Spectral Element Method (LB-DGSEM) auf laminare und turbulente nahezu inkompressible Strömungen im dreidimensionalen Raum**, Master Thesis, University of Cologne, 2018.
3. Dieter Hänel, **Molekulare Gasdynamik**, Springer-Verlag Berlin Heidelberg, 2004 [doi:10.1007/3-540-35047-0](https://doi.org/10.1007/3-540-35047-0)
4. Timm Krüger et al., **The Lattice Boltzmann Method**, Springer International Publishing, 2017 [doi:10.1007/978-3-319-44649-3](https://doi.org/10.1007/978-3-319-44649-3)
