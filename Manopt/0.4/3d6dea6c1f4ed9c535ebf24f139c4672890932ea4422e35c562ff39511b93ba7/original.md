```
LevenbergMarquardt(M, f, jacobian_f, p, num_components=-1)
```

Solve an optimization problem of the form

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \lVert f(p) \rVert^2,
$$

where $f: \mathcal M → ℝ^d$ is a continuously differentiable function, using the Riemannian Levenberg-Marquardt algorithm [Peeters:1993](@cite). The implementation follows Algorithm 1 [AdachiOkunoTakeda:2022](@cite)

# Input

  * `M`:              a manifold $\mathcal M$
  * `f`:              a cost function $f: \mathcal M→ℝ^d$
  * `jacobian_f`:     the Jacobian of $f$. The Jacobian is supposed to accept a keyword argument `basis_domain` which specifies basis of the tangent space at a given point in which the Jacobian is to be calculated. By default it should be the `DefaultOrthonormalBasis`.
  * `p`:              an initial value $p ∈ \mathcal M$
  * `num_components`: length of the vector returned by the cost function (`d`). By default its value is -1 which means that it is determined automatically by calling `f` one additional time. This is only possible when `evaluation` is `AllocatingEvaluation`, for mutating evaluation this value must be explicitly specified.

These can also be passed as a [`NonlinearLeastSquaresObjective`](@ref), then the keyword `jacobian_tangent_basis` below is ignored

# Optional

  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) specify whether the gradient works by allocation (default) form `gradF(M, x)` or [`InplaceEvaluation`](@ref) in place of the form `gradF!(M, X, x)`.
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) a `retraction(M,x,ξ)` to use.
  * `stopping_criterion`:      ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1e-12)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.
  * `expect_zero_residual`:    (`false`) whether or not the algorithm might expect that the value of residual (objective) at minimum is equal to 0.
  * `η`:                       scaling factor for the sufficient cost decrease threshold required to accept new proposal points. Allowed range: `0 < η < 1`.
  * `damping_term_min`:        initial (and also minimal) value of the damping term
  * `β`:                       parameter by which the damping term is multiplied when the current new point is rejected
  * `initial_residual_values`: the initial residual vector of the cost function `f`.
  * `initial_jacobian_f`:      the initial Jacobian of the cost function `f`.
  * `jacobian_tangent_basis`:  an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) specify the basis of the tangent space for `jacobian_f`.

All other keyword arguments are passed to [`decorate_state!`](@ref) for decorators or [`decorate_objective!`](@ref), respectively. If you provide the [`ManifoldGradientObjective`](@ref) directly, these decorations can still be specified

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details

# References
