```
BBMBBMEquations1D(; bathymetry_type = bathymetry_variable,
                  gravity, eta0 = 0.0)
```

BBM-BBM (Benjamin–Bona–Mahony) system in one spatial dimension. The equations for flat bathymetry are given by

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x - \frac{1}{6}D^2\eta_{xxt} &= 0,\\
  v_t + g\eta_x + \left(\frac{1}{2}v^2\right)_x - \frac{1}{6}D^2v_{xxt} &= 0.
\end{aligned}
$$

The unknown quantities of the BBM-BBM equations are the total water height $\eta$ and the velocity $v$. The gravitational acceleration `gravity` is denoted by $g$ and the constant bottom topography (bathymetry) $b = \eta_0 - D$. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$. The BBM-BBM equations are only implemented for $\eta_0 = 0$.

Two types of `bathymetry_type` are supported:

  * [`bathymetry_flat`](@ref): flat bathymetry (typically $b = 0$ everywhere)
  * [`bathymetry_variable`](@ref): general variable bathymetry

For the general case of variable vathymetry the BBM-BBM equations are

$$
\begin{aligned}
  \eta_t + ((\eta + D)v)_x - \frac{1}{6}(D^2\eta_{xt})_x &= 0,\\
  v_t + g\eta_x + \left(\frac{1}{2}v^2\right)_x - \frac{1}{6}(D^2v_t)_{xx} &= 0.
\end{aligned}
$$

One reference for the BBM-BBM system can be found in Bona et al. (1998). The semidiscretization implemented here was developed for flat bathymetry in Ranocha et al. (2020) and generalized for a variable bathymetry in Lampert and Ranocha (2024). It conserves

  * the total water mass (integral of $h$) as a linear invariant
  * the total velocity (integral of $v$) as a linear invariant for flat bathymetry
  * the total energy

for periodic boundary conditions (see Lampert, Ranocha). For reflecting boundary conditions, the semidiscretization conserves

  * the total water (integral of $h$) as a linear invariant
  * the total energy.

Additionally, it is well-balanced for the lake-at-rest stationary solution, see Lampert and Ranocha (2024).

  * Jerry L. Bona, Min Chen (1998) A Boussinesq system for two-way propagation of nonlinear dispersive waves [DOI: 10.1016/S0167-2789(97)00249-2](https://doi.org/10.1016/S0167-2789(97)00249-2)
  * Hendrik Ranocha, Dimitrios Mitsotakis, David I. Ketcheson (2020) A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
  * Joshua Lampert, Hendrik Ranocha (2024) Structure-Preserving Numerical Methods for Two Nonlinear Systems of Dispersive Wave Equations [DOI: 10.48550/arXiv.2402.16669](https://doi.org/10.48550/arXiv.2402.16669)
