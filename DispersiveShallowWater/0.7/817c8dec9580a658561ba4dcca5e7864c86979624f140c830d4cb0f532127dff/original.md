```
HyperbolicSerreGreenNaghdiEquations1D(; bathymetry_type = bathymetry_mild_slope,
                                      gravity,
                                      eta0 = 0.0,
                                      lambda)
```

Hyperbolic approximation of the Serre-Green-Naghdi system in one spatial dimension. The equations for flat bathymetry are given by

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x
    + \biggl( \frac{\lambda}{3} H (1 - H / h) \biggr)_x &= 0,\\
  h w_t + h v w_x &= \lambda (1 - H / h),\\
  H_t + H_x u &= w.
\end{aligned}
$$

The unknown quantities of the hyperbolized Serre-Green-Naghdi equations are the total water height $\eta = h + b$ and the velocity $v$. The gravitational acceleration `gravity` is denoted by $g$ and the bottom topography (bathymetry) $b = \eta_0 - D$. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$. The total water height is therefore given by $\eta = h + b$.

There are two additional variables $w \approx -h v_x$ and $H \approx h$ compared to the [`SerreGreenNaghdiEquations1D`](@ref). In the original papers of Gavrilyuk et al., the variable $H$ is called $\eta$. Here, we use $\eta$ for the total water height and $H$ for auxiliary variable introduced in the hyperbolic approximation.

!!! note "Initial conditions"
    The `HyperbolicSerreGreenNaghdiEquations1D` allow two options for specifying initial conditions:

    1. Returning the full set of variables `q = (η, v, D, w, H)`
    2. Returning a reduced set of variables `q = (η, v, D)` as required for the limit system [`SerreGreenNaghdiEquations1D`](@ref) of the hyperbolic approximation. The remaining variables `w` and `H` are initialized using the default initialization $w \approx -h v_x$ and $H \approx h$ using the derivative operator of the `solver`.


The relaxation parameter `lambda` ($\lambda$) introduced to obtain this hyperbolic approximation of the [`SerreGreenNaghdiEquations1D`](@ref) influences the stiffness of the system. For $\lambda \to \infty$, the hyperbolic Serre-Green-Naghdi equations converge (at least formally) to the original [`SerreGreenNaghdiEquations1D`](@ref). However, the wave speeds of the hyperbolic system increase with increasing $\lambda$, so that explicit time integration methods become more expensive.

Two types of `bathymetry_type` are supported:

  * [`bathymetry_flat`](@ref): flat bathymetry (typically $b = 0$ everywhere)
  * [`bathymetry_mild_slope`](@ref): variable bathymetry with mild-slope approximation

For the mild-slope approximation, the Serre-Green-Naghdi equations are

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x
    + \biggl( \frac{\lambda}{3} H (1 - H / h) \biggr)_x
    + \biggl( g h + \frac{\lambda}{2} (1 - H / h) \biggr) b_x &= 0,\\
  h w_t + h v w_x &= \lambda (1 - H / h),\\
  H_t + H_x u + \frac{3}{2} b_x v &= w.
\end{aligned}
$$

References for the hyperbolized Serre-Green-Naghdi system can be found in

  * Favrie and Gavrilyuk. A rapid numerical method for solving Serre-Green-Naghdi equations describing long free surface gravity waves [DOI: 10.1088/1361-6544/aa712d](https://doi.org/10.1088/1361-6544/aa712d)
  * Busto, Dumbser, Escalante, Favrie, and Gavrilyuk. On High Order ADER Discontinuous Galerkin Schemes for First Order Hyperbolic Reformulations of Nonlinear Dispersive Systems [DOI: 10.1007/s10915-021-01429-8](https://doi.org/10.1007/s10915-021-01429-8)

The semidiscretization implemented here conserves

  * the total water mass (integral of $h$) as a linear invariant
  * the total modified energy

for periodic boundary conditions (see Ranocha and Ricchiuto (2024)). Additionally, it is well-balanced for the lake-at-rest stationary solution, see

  * Hendrik Ranocha and Mario Ricchiuto (2024) Structure-preserving approximations of the Serre-Green-Naghdi equations in standard and hyperbolic form [arXiv: 2408.02665](https://arxiv.org/abs/2408.02665)
