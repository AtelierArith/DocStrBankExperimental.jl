```
AcousticPerturbationEquations2D(v_mean_global, c_mean_global, rho_mean_global)
```

Acoustic perturbation equations (APE) in two space dimensions. The equations are given by

$$
\begin{aligned}
  \frac{\partial\mathbf{v'}}{\partial t} + \nabla (\bar{\mathbf{v}}\cdot\mathbf{v'})
    + \nabla\left( \frac{\bar{c}^2 \tilde{p}'}{\bar{\rho}} \right) &= 0 \\
  \frac{\partial \tilde{p}'}{\partial t} +
    \nabla\cdot (\bar{\rho} \mathbf{v'} + \bar{\mathbf{v}} \tilde{p}') &= 0.
\end{aligned}
$$

The bar $\bar{(\cdot)}$ indicates time-averaged quantities. The unknowns of the APE are the perturbed velocities $\mathbf{v'} = (v_1', v_2')^T$ and the scaled perturbed pressure $\tilde{p}' = \frac{p'}{\bar{c}^2}$, where $p'$ denotes the perturbed pressure and the perturbed variables are defined by $\phi' = \phi - \bar{\phi}$.

In addition to the unknowns, Trixi.jl currently stores the mean values in the state vector, i.e. the state vector used internally is given by

$$
\mathbf{u} =
  \begin{pmatrix}
    v_1' \\ v_2' \\ \tilde{p}' \\ \bar{v}_1 \\ \bar{v}_2 \\ \bar{c} \\ \bar{\rho}
  \end{pmatrix}.
$$

This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the mean values must be zero.
  * The mean values have to be considered when defining initial conditions, boundary conditions or source terms.
  * [`AnalysisCallback`](@ref) analyzes these variables too.
  * Trixi.jl's visualization tools will visualize the mean values by default.

The constructor accepts a 2-tuple `v_mean_global` and scalars `c_mean_global` and `rho_mean_global` which can be used to make the definition of initial conditions for problems with constant mean flow more flexible. These values are ignored if the mean values are defined internally in an initial condition.

The equations are based on the APE-4 system introduced in the following paper:

  * Roland Ewert and Wolfgang Schröder (2003) Acoustic perturbation equations based on flow decomposition via source filtering [DOI: 10.1016/S0021-9991(03)00168-2](https://doi.org/10.1016/S0021-9991(03)00168-2)
