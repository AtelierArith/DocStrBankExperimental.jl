```
trust_regions(M, f, grad_f, hess_f, p=rand(M))
trust_regions(M, f, grad_f, p=rand(M))
```

run the Riemannian trust-regions solver for optimization on manifolds to minimize `f`, see on [AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite).

For the case that no Hessian is provided, the Hessian is computed using finite differences, see [`ApproxHessianFiniteDifference`](@ref). For solving the inner trust-region subproblem of finding an update-vector, by default the [`truncated_conjugate_gradient_descent`](@ref) is used.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f : \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}F : \mathcal M → T \mathcal M$ of $F$
  * `Hess_f`: (optional), the Hessian $\operatorname{Hess}F(x): T_x\mathcal M → T_x\mathcal M$, $X ↦ \operatorname{Hess}F(x)[X] = ∇_ξ\operatorname{grad}f(x)$
  * `p`:      (`rand(M)`) an initial value $x  ∈  \mathcal M$

# Keyword arguments

  * `acceptance_rate`:        Accept/reject threshold: if ρ (the performance ratio for the iterate) is at least the acceptance rate ρ', the candidate is accepted. This value should  be between $0$ and $\frac{1}{4}$
  * `augmentation_threshold`: (`0.75`) trust-region augmentation threshold: if ρ is larger than this threshold, a solution is on the trust region boundary and negative curvature, and the radius is extended (augmented)
  * `augmentation_factor`:    (`2.0`) trust-region augmentation factor
  * `evaluation`:             ([`AllocatingEvaluation`](@ref)) specify whether the gradient and Hessian work by allocation (default) or [`InplaceEvaluation`](@ref) in place
  * `κ`:                      (`0.1`) the linear convergence target rate of the tCG method   [`truncated_conjugate_gradient_descent`](@ref), and is used in a stopping criterion therein
  * `max_trust_region_radius`: the maximum trust-region radius
  * `preconditioner`:          a preconditioner (a symmetric, positive definite operator that should approximate the inverse of the Hessian)
  * `project!`;               (`copyto!`) specify a projection operation for tangent vectors within the subsolver for numerical stability. The required form is `(M, Y, p, X) -> ...` working in place of `Y`.
  * `randomize`;              set to true if the trust-region solve is to be initiated with a random tangent vector and no preconditioner is used.
  * `ρ_regularization`:       (`1e3`) regularize the performance evaluation $ρ$ to avoid numerical inaccuracies.
  * `reduction_factor`:       (`0.25`) trust-region reduction factor
  * `reduction_threshold`:    (`0.1`) trust-region reduction threshold: if ρ is below this threshold, the trust region radius is reduced by `reduction_factor`.
  * `retraction` (`default_retraction_method(M, typeof(p))`) a retraction to use
  * `stopping_criterion`:     ([`StopAfterIteration`](@ref)`(1000) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.
  * `sub_kwargs`:             keyword arguments passed to the sub state and used to decorate the sub options
  * `sub_stopping_criterion`: a stopping criterion for the sub solver, uses the same standard as TCG.
  * `sub_problem`:            ([`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`) problem for the subsolver
  * `sub_state`:              ([`QuasiNewtonState`](@ref)) using [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) and `sub_stopping_criterion` as a stopping criterion. See also `sub_kwargs`.
  * `θ`:                      (`1.0`) 1+θ is the superlinear convergence target rate of the tCG-method [`truncated_conjugate_gradient_descent`](@ref), and is used in a stopping criterion therein
  * `trust_region_radius`:     the initial trust-region radius

For the case that no Hessian is provided, the Hessian is computed using finite difference, see [`ApproxHessianFiniteDifference`](@ref).

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details

# See also

[`truncated_conjugate_gradient_descent`](@ref)
