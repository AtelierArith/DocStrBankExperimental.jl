```
ApproxHessianFiniteDifference{E, P, T, G, RTR, VTR, R <: Real} <: AbstractApproxHessian
```

A functor to approximate the Hessian by a finite difference of gradient evaluation.

Given a point `p` and a direction `X` and the gradient $\operatorname{grad} f(p)$ of a function $f$ the Hessian is approximated as follows: let $c$ be a stepsize, $X ∈ T_{p}\mathcal M$ a tangent vector and $q = \operatorname{retr}_p(\frac{c}{\lVert X \rVert_p}X)$ be a step in direction $X$ of length $c$ following a retraction Then the Hessian is approximated by the finite difference of the gradients, where $\mathcal T_{⋅←⋅}$ is a vector transport.

$$
\operatorname{Hess}f(p)[X] ≈
\frac{\lVert X \rVert_p}{c}\Bigl(
  \mathcal T_{p\gets q}\bigr(\operatorname{grad}f(q)\bigl) - \operatorname{grad}f(p)
\Bigl)
$$

# Fields

  * `gradient!!`:              the gradient function (either allocating or mutating, see `evaluation` parameter)
  * `step_length`:             a step length for the finite difference
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

## Internal temporary fields

  * `grad_tmp`:     a temporary storage for the gradient at the current `p`
  * `grad_dir_tmp`: a temporary storage for the gradient at the current `p_dir`
  * `p_dir::P`:     a temporary storage to the forward direction (or the $q$ in the formula)

# Constructor

```
ApproximateFiniteDifference(M, p, grad_f; kwargs...)
```

## Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `steplength=`2^{-14}$: step length$c`` to approximate the gradient evaluations
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
