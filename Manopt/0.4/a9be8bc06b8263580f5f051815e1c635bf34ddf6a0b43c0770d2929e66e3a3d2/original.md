```
ApproxHessianFiniteDifference{E, P, T, G, RTR, VTR, R <: Real} <: AbstractApproxHessian
```

A functor to approximate the Hessian by a finite difference of gradient evaluation.

Given a point `p` and a direction `X` and the gradient $\operatorname{grad}F: \mathcal M → T\mathcal M$ of a function $F$ the Hessian is approximated as follows: let $c$ be a stepsize, $X∈ T_p\mathcal M$ a tangent vector and $q = \operatorname{retr}_p(\frac{c}{\lVert X \rVert_p}X)$ be a step in direction $X$ of length $c$ following a retraction Then the Hessian is approximated by the finite difference of the gradients, where $\mathcal T_{\cdot\gets\cdot}$ is a vector transport.

$$
\operatorname{Hess}F(p)[X] ≈
\frac{\lVert X \rVert_p}{c}\Bigl(
  \mathcal T_{p\gets q}\bigr(\operatorname{grad}F(q)\bigl) - \operatorname{grad}F(p)
\Bigl)
$$

# Fields

  * `gradient!!`:              the gradient function (either allocating or mutating, see `evaluation` parameter)
  * `step_length`:             a step length for the finite difference
  * `retraction_method`:       a retraction to use
  * `vector_transport_method`: a vector transport to use

## Internal temporary fields

  * `grad_tmp`:     a temporary storage for the gradient at the current `p`
  * `grad_dir_tmp`: a temporary storage for the gradient at the current `p_dir`
  * `p_dir::P`:     a temporary storage to the forward direction (or the $q$ in the formula)

# Constructor

```
ApproximateFiniteDifference(M, p, grad_f; kwargs...)
```

## Keyword arguments

  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) whether the gradient is given as an allocation function or an in-place ([`InplaceEvaluation`](@ref)).
  * `steplength`:              ($2^{-14}$) step length $c$ to approximate the gradient evaluations
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) a `retraction(M, p, X)` to use in the approximation.
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) a vector transport to use
