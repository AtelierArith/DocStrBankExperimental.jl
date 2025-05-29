```
trust_regions!(M, f, grad_f, Hess_f, p; kwargs...)
trust_regions!(M, f, grad_f, p; kwargs...)
```

evaluate the Riemannian trust-regions solver in place of `p`.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f: \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad}f: \mathcal M → T \mathcal M$ of $F$
  * `Hess_f`: (optional) the Hessian $\operatorname{Hess} f$
  * `p`:      an initial value $p  ∈  \mathcal M$

For the case that no Hessian is provided, the Hessian is computed using finite difference, see [`ApproxHessianFiniteDifference`](@ref).

for more details and all options, see [`trust_regions`](@ref)
