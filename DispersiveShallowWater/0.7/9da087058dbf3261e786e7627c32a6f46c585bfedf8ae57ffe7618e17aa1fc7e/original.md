```
SvaerdKalischEquations1D(; bathymetry_type = bathymetry_variable, gravity,
                         eta0 = 0.0, alpha = 0.0, beta = 1/3, gamma = 0.0)
```

Dispersive system by Svärd and Kalisch (2023) in one spatial dimension. The equations for variable bathymetry are given in conservative variables by

$$
\begin{aligned}
  h_t + (hv)_x &= (\hat\alpha(\hat\alpha(h + b)_x)_x)_x,\\
  (hv)_t + (hv^2)_x + gh(h + b)_x &= (\hat\alpha v(\hat\alpha(h + b)_x)_x)_x + (\hat\beta v_x)_{xt} + \frac{1}{2}(\hat\gamma v_x)_{xx} + \frac{1}{2}(\hat\gamma v_{xx})_x,
\end{aligned}
$$

where $\hat\alpha^2 = \alpha\sqrt{gD}D^2$, $\hat\beta = \beta D^3$, $\hat\gamma = \gamma\sqrt{gD}D^3$. The coefficients $\alpha$, $\beta$ and $\gamma$ are provided in dimensionless form and $D = \eta_0 - b$ is the still-water depth and `eta0` is the still-water surface (lake-at-rest). The equations can be rewritten in primitive variables as

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x &= (\hat\alpha(\hat\alpha\eta_x)_x)_x,\\
  v_t(\eta + D) - v((\eta + D)v)_x + ((\eta + D)v^2)_x + g(\eta + D)\eta_x &= (\hat\alpha v(\hat\alpha\eta_x)_x)_x - v(\hat\alpha(\hat\alpha\eta_x)_x)_x + (\hat\beta v_x)_{xt} + \frac{1}{2}(\hat\gamma v_x)_{xx} + \frac{1}{2}(\hat\gamma v_{xx})_x.
\end{aligned}
$$

The unknown quantities of the Svärd-Kalisch equations are the total water height $\eta$ and the velocity $v$. The gravitational acceleration `gravity` is denoted by $g$ and the bottom topography (bathymetry) $b = \eta_0 - D$. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$.

Currently, the equations only support a general variable bathymetry, see [`bathymetry_variable`](@ref).

`SvärdKalischEquations1D` is an alias for `SvaerdKalischEquations1D`.

The equations by Svärd and Kalisch are presented and analyzed in Svärd and Kalisch (2025). The semidiscretization implemented here conserves

  * the total water mass (integral of $h$) as a linear invariant
  * the total momentum (integral of $h v$) as a nonlinear invariant for flat bathymetry
  * the total modified energy

for periodic boundary conditions (see Lampert, Ranocha). Additionally, it is well-balanced for the lake-at-rest stationary solution, see Lampert and Ranocha (2024).

  * Magnus Svärd, Henrik Kalisch (2025) A novel energy-bounded Boussinesq model and a well-balanced and stable numerical discretization [arXiv: 2302.09924](https://arxiv.org/abs/2302.09924), [DOI: 10.1016/j.jcp.2024.113516](https://doi.org/10.1016/j.jcp.2024.113516)
  * Joshua Lampert, Hendrik Ranocha (2024) Structure-Preserving Numerical Methods for Two Nonlinear Systems of Dispersive Wave Equations [DOI: 10.48550/arXiv.2402.16669](https://doi.org/10.48550/arXiv.2402.16669)
