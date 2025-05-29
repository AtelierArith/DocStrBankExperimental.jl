```
TangentDynamicalSystem <: DynamicalSystem
TangentDynamicalSystem(ds::CoreDynamicalSystem; kwargs...)
```

A dynamical system that bundles the evolution of `ds` (which must be an [`CoreDynamicalSystem`](@ref)) and `k` deviation vectors that are evolved according to the *dynamics in the tangent space* (also called linearized dynamics or the tangent dynamics).

The state of `ds` **must** be an `AbstractVector` for `TangentDynamicalSystem`.

`TangentDynamicalSystem` follows the [`DynamicalSystem`](@ref) interface with the following adjustments:

  * `reinit!` takes an additional keyword `Q0` (with same default as below)
  * The additional functions [`current_deviations`](@ref) and [`set_deviations!`](@ref) are provided for the deviation vectors.

## Keyword arguments

  * `k` or `Q0`: `Q0` represents the initial deviation vectors (each column = 1 vector). If `k::Int` is given, a matrix `Q0` is created with the first `k` columns of the identity matrix. Otherwise `Q0` can be given directly as a matrix. It must hold that `size(Q, 1) == dimension(ds)`. You can use [`orthonormal`](@ref) for random orthonormal vectors. By default `k = dimension(ds)` is used.
  * `u0 = current_state(ds)`: Starting state.
  * `J` and `J0`: See section "Jacobian" below.

## Description

Let $u$ be the state of `ds`, and $y$ a deviation (or perturbation) vector. These two are evolved in parallel according to

$$
\begin{array}{rcl}
\frac{d\vec{x}}{dt} &=& f(\vec{x}) \\
\frac{dY}{dt} &=& J_f(\vec{x}) \cdot Y
\end{array}
\quad \mathrm{or}\quad
\begin{array}{rcl}
\vec{x}_{n+1} &=& f(\vec{x}_n) \\
Y_{n+1} &=& J_f(\vec{x}_n) \cdot Y_n.
\end{array}
$$

for continuous or discrete time respectively. Here $f$ is the [`dynamic_rule`](@ref)`(ds)` and $J_f$ is the Jacobian of $f$.

## Jacobian

The keyword `J` provides the Jacobian function. It must be a Julia function in the same form as `f`, the [`dynamic_rule`](@ref). Specifically, `J(u, p, n) -> M::SMatrix` for the out-of-place version or `J(M, u, p, n)` for the in-place version acting in-place on `M`. In both cases `M` is the Jacobian matrix used for the evolution of the deviation vectors.

By default `J = nothing`.  In this case `J` is constructed automatically using the module [`ForwardDiff`](https://github.com/JuliaDiff/ForwardDiff.jl), hence its limitations also apply here. Even though `ForwardDiff` is very fast, depending on your exact system you might gain significant speed-up by providing a hand-coded Jacobian and so it is recommended. Additionally, automatic and in-place Jacobians cannot be time dependent.

The keyword `J0` allows you to pass an initialized Jacobian matrix `J0`. This is useful for large in-place systems where only a few components of the Jacobian change during the time evolution. `J0` can be a sparse or any other matrix type. If not given, a matrix of zeros is used. `J0` is ignored for out of place systems.
