```
ImplicitFreeSurface(; solver_method=:Default, gravitational_acceleration=g_Earth, solver_settings...)
```

Return an implicit free-surface solver. The implicit free-surface equation is

$$
\left [ 𝛁_h ⋅ (H 𝛁_h) - \frac{1}{g Δt^2} \right ] η^{n+1} = \frac{𝛁_h ⋅ 𝐐_⋆}{g Δt} - \frac{η^{n}}{g Δt^2} ,
$$

where $η^n$ is the free-surface elevation at the $n$-th time step, $H$ is depth, $g$ is the gravitational acceleration, $Δt$ is the time step, $𝛁_h$ is the horizontal gradient operator, and $𝐐_⋆$ is the barotropic volume flux associated with the predictor velocity field $𝐮_⋆$, i.e.,

$$
𝐐_⋆ = \int_{-H}^0 𝐮_⋆ \, 𝖽 z ,
$$

where

$$
𝐮_⋆ = 𝐮^n + \int_{t_n}^{t_{n+1}} 𝐆ᵤ \, 𝖽t .
$$

This equation can be solved, in general, using the [`ConjugateGradientSolver`](@ref) but other solvers can be invoked in special cases.

If $H$ is constant, we divide through out to obtain

$$
\left ( ∇^2_h - \frac{1}{g H Δt^2} \right ) η^{n+1}  = \frac{1}{g H Δt} \left ( 𝛁_h ⋅ 𝐐_⋆ - \frac{η^{n}}{Δt} \right ) .
$$

Thus, for constant $H$ and on grids with regular spacing in $x$ and $y$ directions, the free surface can be obtained using the [`FFTBasedPoissonSolver`](@ref).

`solver_method` can be either of:

  * `:FastFourierTransform` for [`FFTBasedPoissonSolver`](@ref)
  * `:HeptadiagonalIterativeSolver`  for [`HeptadiagonalIterativeSolver`](@ref)
  * `:PreconditionedConjugateGradient` for [`ConjugateGradientSolver`](@ref)

By default, if the grid has regular spacing in the horizontal directions then the `:FastFourierTransform` is chosen, otherwise the `:HeptadiagonalIterativeSolver`.
