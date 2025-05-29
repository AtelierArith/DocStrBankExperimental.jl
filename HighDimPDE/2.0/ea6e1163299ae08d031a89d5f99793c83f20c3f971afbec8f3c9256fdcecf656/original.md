```julia
ParabolicPDEProblem(
    μ,
    σ,
    x0,
    tspan;
    g,
    f,
    p,
    xspan,
    x0_sample,
    neumann_bc,
    payoff,
    kw...
)

```

Defines a Parabolic Partial Differential Equation of the form:

$$
\begin{aligned}
    \frac{du}{dt} &= \tfrac{1}{2} \text{Tr}(\sigma \sigma^T) \Delta u(x, t) + \mu \nabla u(x, t) \\
    &\quad +  f(x, u(x, t), ( \nabla_x u )(x, t), p, t)
\end{aligned}
$$

  * Semilinear Parabolic Partial Differential Equation 

      * f -> f(X, u, σᵀ∇u, p, t)
  * Kolmogorov Differential Equation

      * f -> `nothing`
      * x0 -> nothing, xspan must be provided.
  * Obstacle Partial Differential Equation 

      * f -> `nothing`
      * g -> `nothing`
      * discounted payoff function provided.

## Arguments

  * `μ` : drift function, of the form `μ(x, p, t)`.
  * `σ` : diffusion function `σ(x, p, t)`.
  * `x`: point where `u(x,t)` is approximated. Is required even in the case where `x0_sample` is provided. Determines the dimensionality of the PDE.
  * `tspan`: timespan of the problem.
  * `g` : initial condition, of the form `g(x, p, t)`.
  * `f` : nonlinear function, of the form  `f(X, u, σᵀ∇u, p, t)`

## Optional Arguments

  * `p`: the parameter vector.
  * `x0_sample` : sampling method for `x0`. Can be `UniformSampling(a,b)`, `NormalSampling(σ_sampling, shifted)`, or `NoSampling` (by default). If `NoSampling`, only solution at the single point `x` is evaluated.
  * `neumann_bc`: if provided, Neumann boundary conditions on the hypercube `neumann_bc[1] × neumann_bc[2]`.
  * `xspan`: The domain of the independent variable `x`
  * `payoff`: The discounted payoff function. Required when solving for optimal stopping problem (Obstacle PDEs).
