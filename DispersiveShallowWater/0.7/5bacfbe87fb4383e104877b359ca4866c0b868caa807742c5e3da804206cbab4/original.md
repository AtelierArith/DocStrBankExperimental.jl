```
BBMEquation1D(; gravity, D = 1.0, eta0 = 0.0, split_form = true)
```

BBM (Benjamin–Bona–Mahony) equation in one spatial dimension. The equation is given by

$$
\begin{aligned}
  \eta_t + \sqrt{gD}\eta_x + \frac{3}{2}\sqrt{\frac{g}{D}}\eta\eta_x - \frac{1}{6}D^2\eta_{xxt} &= 0.
\end{aligned}
$$

The unknown quantity of the BBM equation is the total water height $\eta$. The gravitational acceleration `gravity` is denoted by $g$ and the constant bottom topography (bathymetry) $b = \eta_0 - D$, where $\eta_0$ is the constant still-water surface and $D$ the still-water depth. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$. The BBM equation is only implemented for $\eta_0 = 0$.

The equations only support a flat bathymetry.

The BBM equation is first described in Benjamin, Bona, and Mahony (1972). The semidiscretization implemented here is developed in Ranocha, Mitsotakis, and Ketcheson (2020) for `split_form = true` and in Linders, Ranocha, and Birken (2023) for `split_form = false`. If `split_form` is `true`, a split form in the semidiscretization is used, which conserves

  * the total water mass (integral of $h$) as a linear invariant
  * a quadratic invariant (integral of $1/2\eta(\eta - 1/6D^2\eta_{xx})$ or for periodic boundary conditions equivalently $1/2(\eta^2 + 1/6D^2\eta_x^2)$), which is called here [`energy_total_modified`](@ref) (and [`entropy_modified`](@ref)) because it contains derivatives of the solution

for periodic boundary conditions. If `split_form` is `false` the semidiscretization conserves

  * the total water mass (integral of $h$) as a linear invariant
  * the Hamiltonian (integral of $1/4\sqrt{g/D}\eta^3 + 1/2\sqrt{gD}\eta^2$) (see [`hamiltonian`](@ref))

for periodic boundary conditions.

  * Thomas B. Benjamin, Jerry L. Bona and John J. Mahony (1972) Model equations for long waves in nonlinear dispersive systems [DOI: 10.1098/rsta.1972.0032](https://doi.org/10.1098/rsta.1972.0032)
  * Hendrik Ranocha, Dimitrios Mitsotakis and David I. Ketcheson (2020) A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
  * Viktor Linders, Hendrik Ranocha and Philipp Birken (2023) Resolving entropy growth from iterative methods [DOI: 10.1007/s10543-023-00992-w](https://doi.org/10.1007/s10543-023-00992-w)
