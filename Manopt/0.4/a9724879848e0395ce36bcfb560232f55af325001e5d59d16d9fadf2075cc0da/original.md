```
adaptive_regularization_with_cubics!(M, f, grad_f, Hess_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, mho, p; kwargs...)
```

evaluate the Riemannian adaptive regularization with cubics solver in place of `p`.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $F: \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}F: \mathcal M → T \mathcal M$ of $F$
  * `Hess_f`: (optional) the Hessian $H( \mathcal M, x, ξ)$ of $F$
  * `p`:      an initial value $p  ∈  \mathcal M$

For the case that no Hessian is provided, the Hessian is computed using finite difference, see [`ApproxHessianFiniteDifference`](@ref).

the cost `f` and its gradient and Hessian might also be provided as a [`ManifoldHessianObjective`](@ref)

for more details and all options, see [`adaptive_regularization_with_cubics`](@ref).
