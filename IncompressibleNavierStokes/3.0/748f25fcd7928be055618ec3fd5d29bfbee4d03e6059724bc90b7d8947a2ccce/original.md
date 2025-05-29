```julia
struct OneLegMethod{T, M} <: IncompressibleNavierStokes.AbstractODEMethod{T}
```

Explicit one-leg β-method following symmetry-preserving discretization of turbulent flow. See Verstappen and Veldman [Verstappen2003](@cite) [Verstappen1997](@cite) for details.

We here require that the time step $\Delta t$ is constant. Given the velocity $u_0$ and pressure $p_0$ at the current time $t_0$ and their previous values $u_{-1}$ and $p_{-1}$ at the time $t_{-1} = t_0 - \Delta t$, we start by computing the "offstep" values $v = (1 + \beta) v_0 - \beta v_{-1}$ and $Q = (1 + \beta) p_0 - \beta p_{-1}$ for some $\beta = \frac{1}{2}$.

A tentative velocity field $\tilde{v}$ is then computed as follows:

$$
\tilde{v} = \frac{1}{\beta + \frac{1}{2}} \left( 2 \beta u_0 - \left( \beta -
\frac{1}{2} \right) u_{-1} + \Delta t F(v, t) - \Delta t
(G Q + y_G(t)) \right).
$$

A pressure correction $\Delta p$ is obtained by solving the Poisson equation

$$
L \Delta p = \frac{\beta + \frac{1}{2}}{\Delta t} W (M \tilde{v} + y_M(t)).
$$

Finally, the divergence free velocity field is given by

$$
u = \tilde{v} - \frac{\Delta t}{\beta + \frac{1}{2}} G \Delta p,
$$

while the second order accurate pressure is given by

$$
p = 2 p_0 - p_{-1} + \frac{4}{3} \Delta p.
$$

## Fields

  * `β`
  * `p_add_solve`
  * `method_startup`
