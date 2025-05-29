```
ShallowWaterExnerEquations1D(;gravity, H0 = 0.0,
                             friction = ManningFriction(n = 0.0),
                             sediment_model,
                             porosity,
                             rho_f, rho_s)
```

Formulation of the Shallow water-Exner equations in one space dimension that possesses a mathematical entropy inequality. The equations are given by

$$
\begin{cases}
\partial_t h + \partial_x hv = 0, \\
\partial_t hv + \partial_x (hv^2) + gh\partial_x (h + h_b) + g\frac{1}{r}h_s\partial_x (rh + h_b) + \frac{\tau}{\rho_f} = 0,\\
\partial_t h_b + \partial_x q_s = 0,
\end{cases}
$$

The unknown quantities are the water and sediment height $h$, $h_b$ and the velocity $v$. The sediment discharge $q_s(h, hv)$ is determined by the `sediment_model` and is used to determine the active sediment height $h_s = q_s / v$. Furthermore $\tau$ denotes the shear stress at the water-sediment interface and is determined by the `friction` model. The gravitational acceleration is denoted by $g$, and $\rho_f$ and $\rho_s$ are the fluid and sediment densities, respectively. The density ratio is given by $r = \rho_f / \rho_s$, where $r$ lies between $0 < r < 1$ as the fluid density $\rho_f$ should be smaller than the sediment density $\rho_s$.

The conservative variable water height $h$ is measured from the sediment height $h_b$, therefore one also defines the total water height as $H = h + h_b$.

The additional quantity $H_0$ is also available to store a reference value for the total water height that is useful to set initial conditions or test the "lake-at-rest" well-balancedness.

The entropy conservative formulation has been derived in the paper:

  * E.D. Fernández-Nieto, T.M. de Luna, G. Narbona-Reina and J. de Dieu Zabsonré (2017)
    Formal deduction of the Saint-Venant–Exner model including arbitrarily sloping sediment beds and associated energy
    [DOI: 10.1051/m2an/2016018](https://doi.org/10.1051/m2an/2016018)
