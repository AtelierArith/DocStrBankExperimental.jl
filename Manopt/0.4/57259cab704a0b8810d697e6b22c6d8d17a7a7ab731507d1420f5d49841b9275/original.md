```
truncated_conjugate_gradient_descent(M, f, grad_f, p; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, mho::ManifoldHessianObjective, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, trmo::TrustRegionModelObjective, p, X; kwargs...)
```

solve the trust-region subproblem

$$
\begin{align*}
\operatorname*{arg\,min}_{Y  ∈  T_p\mathcal{M}}&\ m_p(Y) = f(p) +
⟨\operatorname{grad}f(p), Y⟩_p + \frac{1}{2} ⟨\mathcal{H}_p[Y], Y⟩_p\\
\text{such that}& \ \lVert Y \rVert_p ≤ Δ
\end{align*}
$$

on a manifold M by using the Steihaug-Toint truncated conjugate-gradient (tCG) method. For a description of the algorithm and theorems offering convergence guarantees, see [AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite).

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f: \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}f: \mathcal M → T\mathcal M$ of `F`
  * `Hess_f`: (optional, cf. [`ApproxHessianFiniteDifference`](@ref)) the Hessian $\operatorname{Hess}f: T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}F(p)[X] = ∇_X\operatorname{grad}f(p)$
  * `p`:      a point on the manifold $p ∈ \mathcal M$
  * `X`:      an initial tangential vector $X ∈ T_p\mathcal M$

Instead of the three functions, you either provide a [`ManifoldHessianObjective`](@ref) `mho` which is then used to build the trust region model, or a [`TrustRegionModelObjective`](@ref) `trmo` directly.

# Optional

  * `evaluation`:          ([`AllocatingEvaluation`](@ref)) specify whether the gradient and Hessian work by  allocation (default) or [`InplaceEvaluation`](@ref) in place
  * `preconditioner`:      a preconditioner for the Hessian H
  * `θ`:                   (`1.0`) 1+θ is the superlinear convergence target rate.
  * `κ`:                   (`0.1`) the linear convergence target rate.
  * `randomize`:           set to true if the trust-region solve is initialized to a random tangent vector. This disables preconditioning.
  * `trust_region_radius`: (`injectivity_radius(M)/4`) a trust-region radius
  * `project!`:            (`copyto!`) for numerical stability it is possible to project onto the tangent space after every iteration. By default this only copies instead.
  * `stopping_criterion`:  ([`StopAfterIteration`](@ref)`(manifol_dimension(M)) |`[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(;κ=κ, θ=θ) |`[`StopWhenCurvatureIsNegative`](@ref)`() |`[`StopWhenTrustRegionIsExceeded`](@ref)`() |`[`StopWhenModelIncreased`](@ref)`()`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop,

and the ones that are passed to [`decorate_state!`](@ref) for decorators.

# Output

the obtained (approximate) minimizer $Y^*$, see [`get_solver_return`](@ref) for details

# See also

[`trust_regions`](@ref)
