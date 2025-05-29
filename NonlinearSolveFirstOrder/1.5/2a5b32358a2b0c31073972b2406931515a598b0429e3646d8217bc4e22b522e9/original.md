```
LevenbergMarquardt(;
    linsolve = nothing,
    damping_initial::Real = 1.0, α_geodesic::Real = 0.75, disable_geodesic = Val(false),
    damping_increase_factor::Real = 2.0, damping_decrease_factor::Real = 3.0,
    finite_diff_step_geodesic = 0.1, b_uphill::Real = 1.0, min_damping_D::Real = 1e-8,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

An advanced Levenberg-Marquardt implementation with the improvements suggested in [transtrum2012improvements](@citet). Designed for large-scale and numerically-difficult nonlinear systems.

### Keyword Arguments

  * `damping_initial`: the starting value for the damping factor. The damping factor is inversely proportional to the step size. The damping factor is adjusted during each iteration. Defaults to `1.0`. See Section 2.1 of [transtrum2012improvements](@citet).
  * `damping_increase_factor`: the factor by which the damping is increased if a step is rejected. Defaults to `2.0`. See Section 2.1 of [transtrum2012improvements](@citet).
  * `damping_decrease_factor`: the factor by which the damping is decreased if a step is accepted. Defaults to `3.0`. See Section 2.1 of [transtrum2012improvements](@citet).
  * `min_damping_D`: the minimum value of the damping terms in the diagonal damping matrix `DᵀD`, where `DᵀD` is given by the largest diagonal entries of `JᵀJ` yet encountered, where `J` is the Jacobian. It is suggested by [transtrum2012improvements](@citet) to use a minimum value of the elements in `DᵀD` to prevent the damping from being too small. Defaults to `1e-8`.
  * `disable_geodesic`: Disables Geodesic Acceleration if set to `Val(true)`. It provides a way to trade-off robustness for speed, though in most situations Geodesic Acceleration should not be disabled.

For the remaining arguments, see [`GeodesicAcceleration`](@ref) and [`NonlinearSolveFirstOrder.LevenbergMarquardtTrustRegion`](@ref) documentations.
