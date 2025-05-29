```
bopik(xae, xes)
```

Computes Öpik's coordinates of impact parameter vector $\mathbf{B}$ in hyperbolic planetary close encounter. Returns a named tuple with the following fields:

  * `ξ` = $\mathbf{B}\cdot\hat{\mathbf{\xi}}/R_E$ and `ζ` = $\mathbf{B}\cdot\hat{\mathbf{\zeta}}/R_E$, where $\mathbf{B}$ is the impact parameter vector, $(\hat{\mathbf{\xi}}, \hat{\mathbf{\zeta}})$ is Öpik's frame and $R_E$ is the Earth's radius in au.
  * `U` is another named tuple with the following fields:

      * `y` = $U_y$.
      * `norm` = $||\mathbf{U}||$ where $\mathbf{U}$ is the planetocentric velocity vector in km/s.
  * `b` = $b_E$, where $b_E$ is the Earth impact cross section ("critical B"). See [`crosssection`](@ref).

# Arguments

  * `xae`: asteroid's geocentric position/velocity vector at closest approach in au, au/day.
  * `xes`: planet's heliocentric position/velocity vector at asteroid's closest approach in au, au/day.

!!! reference
    See equations (37)-(38) in page 14 of https://doi.org/10.1007/s10569-019-9914-4.

