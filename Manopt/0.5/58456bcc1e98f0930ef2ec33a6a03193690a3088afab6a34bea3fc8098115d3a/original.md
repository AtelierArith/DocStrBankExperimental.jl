```
trust_regions(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
trust_regions(M, f, grad_f, p=rand(M); kwargs...)
trust_regions!(M, f, grad_f, Hess_f, p; kwargs...)
trust_regions!(M, f, grad_f, p; kwargs...)
```

run the Riemannian trust-regions solver for optimization on manifolds to minimize `f`, see on [AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite).

For the case that no Hessian is provided, the Hessian is computed using finite differences, see [`ApproxHessianFiniteDifference`](@ref). For solving the inner trust-region subproblem of finding an update-vector, by default the [`truncated_conjugate_gradient_descent`](@ref) is used.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `Hess_f`: the (Riemannian) Hessian $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ of f as a function `(M, p, X) -> Y` or a function `(M, Y, p, X) -> Y` computing `Y` in-place
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

  * `acceptance_rate`:        accept/reject threshold: if ρ (the performance ratio for the iterate) is at least the acceptance rate ρ', the candidate is accepted. This value should  be between $0$ and $rac{1}{4}$
  * `augmentation_threshold=0.75`: trust-region augmentation threshold: if ρ is larger than this threshold, a solution is on the trust region boundary and negative curvature, and the radius is extended (augmented)
  * `augmentation_factor=2.0`: trust-region augmentation factor
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `κ=0.1`: the linear convergence target rate of the tCG method   [`truncated_conjugate_gradient_descent`](@ref), and is used in a stopping criterion therein
  * `max_trust_region_radius`: the maximum trust-region radius
  * `preconditioner`:       a preconditioner for the Hessian H. This is either an allocating function `(M, p, X) -> Y` or an in-place function `(M, Y, p, X) -> Y`, see `evaluation`, and by default set to the identity.
  * `project!=copyto!`: for numerical stability it is possible to project onto the tangent space after every iteration. the function has to work inplace of `Y`, that is `(M, Y, p, X) -> Y`, where `X` and `Y` can be the same memory.
  * `randomize=false`:      indicate whether `X` is initialised to a random vector or not. This disables preconditioning.
  * `ρ_regularization=1e3`: regularize the performance evaluation $ρ$ to avoid numerical inaccuracies.
  * `reduction_factor=0.25`: trust-region reduction factor
  * `reduction_threshold=0.1`: trust-region reduction threshold: if ρ is below this threshold, the trust region radius is reduced by `reduction_factor`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: a functor indicating that the stopping criterion is fulfilled
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_stopping_criterion=`( see [`truncated_conjugate_gradient_descent`](@ref)): a functor indicating that the stopping criterion is fulfilled
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`[`QuasiNewtonState`](@ref):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function. where [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) is used
  * `θ=1.0`:                the superlinear convergence target rate of $1+θ$ of the tCG-method [`truncated_conjugate_gradient_descent`](@ref), and is used in a stopping criterion therein
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: the initial trust-region radius

For the case that no Hessian is provided, the Hessian is computed using finite difference, see [`ApproxHessianFiniteDifference`](@ref).

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.

# See also

[`truncated_conjugate_gradient_descent`](@ref)
