```
truncated_conjugate_gradient_descent!(M, f, grad_f, Hess_f, p, X; kwargs...)
truncated_conjugate_gradient_descent!(M, f, grad_f, p, X; kwargs...)
```

solve the trust-region subproblem in place of `X` (and `p`).

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $F: \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}f: \mathcal M → T\mathcal M$ of `f`
  * `Hess_f`: the Hessian $\operatorname{Hess}f(x): T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}f(p)[X]$
  * `p`:      a point on the manifold $p ∈ \mathcal M$
  * `X`:      an update tangential vector $X ∈ T_x\mathcal M$

For more details and all optional arguments, see [`truncated_conjugate_gradient_descent`](@ref).
