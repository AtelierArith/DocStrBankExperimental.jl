```julia
PIDEProblem(
    μ,
    σ,
    x0,
    tspan,
    g,
    f;
    p,
    x0_sample,
    neumann_bc,
    kw...
)

```

Defines a Partial Integro Differential Problem, of the form

$$
\begin{aligned}
    \frac{du}{dt} &= \tfrac{1}{2} \text{Tr}(\sigma \sigma^T) \Delta u(x, t) + \mu \nabla u(x, t) \\
    &\quad + \int f(x, y, u(x, t), u(y, t), ( \nabla_x u )(x, t), ( \nabla_x u )(y, t), p, t) dy,
\end{aligned}
$$

with $u(x,0) = g(x)$.

## Arguments

  * `g` : initial condition, of the form `g(x, p, t)`.
  * `f` : nonlinear function, of the form `f(x, y, u(x, t), u(y, t), ∇u(x, t), ∇u(y, t), p, t)`.
  * `μ` : drift function, of the form `μ(x, p, t)`.
  * `σ` : diffusion function `σ(x, p, t)`.
  * `x`: point where `u(x,t)` is approximated. Is required even in the case where `x0_sample` is provided. Determines the dimensionality of the PDE.
  * `tspan`: timespan of the problem.
  * `p`: the parameter vector.
  * `x0_sample` : sampling method for `x0`. Can be `UniformSampling(a,b)`, `NormalSampling(σ_sampling, shifted)`, or `NoSampling` (by default). If `NoSampling`, only solution at the single point `x` is evaluated.
  * `neumann_bc`: if provided, Neumann boundary conditions on the hypercube `neumann_bc[1] × neumann_bc[2]`.
