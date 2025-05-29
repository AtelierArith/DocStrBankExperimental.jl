```
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p=rand(M), X=rand(M); vector_at=p);
    kwargs...
)
truncated_conjugate_gradient_descent(M, mho::ManifoldHessianObjective, p=rand(M), X=rand(M; vector_at=p);
    kwargs...
)
truncated_conjugate_gradient_descent(M, trmo::TrustRegionModelObjective, p=rand(M), X=rand(M; vector_at=p);
    kwargs...
)
```

solve the trust-region subproblem

$$
\begin{align*}
\operatorname*{arg\,min}_{Y  ∈  T_p\mathcal{M}}&\ m_p(Y) = f(p) +
⟨\operatorname{grad}f(p), Y⟩_p + \frac{1}{2} ⟨\mathcal{H}_p[Y], Y⟩_p\\
\text{such that}& \ \lVert Y \rVert_p ≤ Δ
\end{align*}
$$

on a manifold $\mathcal M$ by using the Steihaug-Toint truncated conjugate-gradient (tCG) method. This can be done inplace of `X`.

For a description of the algorithm and theorems offering convergence guarantees, see [AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite).

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `Hess_f`: the (Riemannian) Hessian $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ of f as a function `(M, p, X) -> Y` or a function `(M, Y, p, X) -> Y` computing `Y` in-place
  * `p`: a point on the manifold $\mathcal M$
  * `X`: a tangent vector at the point $p$ on the manifold $\mathcal M$

Instead of the three functions, you either provide a [`ManifoldHessianObjective`](@ref) `mho` which is then used to build the trust region model, or a [`TrustRegionModelObjective`](@ref) `trmo` directly.

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `preconditioner`:       a preconditioner for the Hessian H. This is either an allocating function `(M, p, X) -> Y` or an in-place function `(M, Y, p, X) -> Y`, see `evaluation`, and by default set to the identity.
  * `θ=1.0`:                the superlinear convergence target rate of $1+θ$
  * `κ=0.1`:                the linear convergence target rate.
  * `project!=copyto!`: for numerical stability it is possible to project onto the tangent space after every iteration. the function has to work inplace of `Y`, that is `(M, Y, p, X) -> Y`, where `X` and `Y` can be the same memory.
  * `randomize=false`:      indicate whether `X` is initialised to a random vector or not. This disables preconditioning.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(base_manifold(Tpm))``)`[`|`](@ref StopWhenAny)[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(; κ=κ, θ=θ)`[`|`](@ref StopWhenAny)[`StopWhenTrustRegionIsExceeded`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenCurvatureIsNegative`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenModelIncreased`](@ref)`()`: a functor indicating that the stopping criterion is fulfilled
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: the initial trust-region radius

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.

# See also

[`trust_regions`](@ref)
