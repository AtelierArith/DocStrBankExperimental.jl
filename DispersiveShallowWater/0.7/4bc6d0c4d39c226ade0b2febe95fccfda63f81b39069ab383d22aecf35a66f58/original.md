```
SerreGreenNaghdiEquations1D(; bathymetry_type = bathymetry_variable,
                            gravity, eta0 = 0.0)
```

Serre-Green-Naghdi system in one spatial dimension. The equations for flat bathymetry are given by

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x + p_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}.
\end{aligned}
$$

The unknown quantities of the Serre-Green-Naghdi equations are the total water height $\eta = h + b$ and the velocity $v$. The gravitational acceleration `gravity` is denoted by $g$ and the bottom topography (bathymetry) $b = \eta_0 - D$. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$. The total water height is therefore given by $\eta = h + b$.

Three types of `bathymetry_type` are supported:

  * [`bathymetry_flat`](@ref): flat bathymetry (typically $b = 0$ everywhere)
  * [`bathymetry_mild_slope`](@ref): variable bathymetry with mild-slope approximation
  * [`bathymetry_variable`](@ref): general variable bathymetry

For the mild-slope approximation, the Serre-Green-Naghdi equations are

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} (h^2 b_x v_t)_x - \frac{1}{2} h^2 b_x v_{tx} + \frac{3}{4} h b_x^2 v_t
    + \frac{1}{2} g (h^2)_x + g h b_x + \frac{1}{2} h (v^2)_x
    + p_x + \frac{3}{2} \frac{p}{h} b_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}
    + \frac{1}{2} h^2 v (b_x v)_x.
\end{aligned}
$$

For the general case of variable bathymetry without mild-slope approximation, the Serre-Green-Naghdi equations are

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t - \frac{1}{3} (h^3 v_{tx})_x + \frac{1}{2} (h^2 b_x v_t)_x - \frac{1}{2} h^2 b_x v_{tx} + h b_x^2 v_t
    + \frac{1}{2} g (h^2)_x + g h b_x + \frac{1}{2} h (v^2)_x
    + p_x + \frac{3}{2} \frac{p}{h} b_x + \psi b_x &= 0,\\
  p &= \frac{1}{3} h^3 v_{x}^2 - \frac{1}{3} h^3 v v_{xx}
    + \frac{1}{2} h^2 v (b_x v)_x,\\
  \psi &= \frac{1}{4} h v (b_x v)_x.
\end{aligned}
$$

References for the Serre-Green-Naghdi system can be found in

  * Serre (1953) Contribution â l'étude des écoulements permanents et variables dans les canaux [DOI: 10.1051/lhb/1953034](https://doi.org/10.1051/lhb/1953034)
  * Green and Naghdi (1976) A derivation of equations for wave propagation in water of variable depth [DOI: 10.1017/S0022112076002425](https://doi.org/10.1017/S0022112076002425)

The semidiscretization implemented here conserves

  * the total water mass (integral of $h$) as a linear invariant
  * the total momentum (integral of $h v$) as a nonlinear invariant if the bathymetry is constant
  * the total modified energy

for periodic boundary conditions (see Ranocha and Ricchiuto (2024)). Additionally, it is well-balanced for the lake-at-rest stationary solution, see

  * Hendrik Ranocha and Mario Ricchiuto (2024) Structure-preserving approximations of the Serre-Green-Naghdi equations in standard and hyperbolic form [arXiv: 2408.02665](https://arxiv.org/abs/2408.02665)
