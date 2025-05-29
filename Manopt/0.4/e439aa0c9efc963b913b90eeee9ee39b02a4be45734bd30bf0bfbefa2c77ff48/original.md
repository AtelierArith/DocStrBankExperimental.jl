```
alternating_gradient_descent!(M::ProductManifold, f, grad_f, p)
alternating_gradient_descent!(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

perform a alternating gradient descent in place of `p`.

# Input

  * `M`:      a product manifold $\mathcal M$
  * `f`:      the objective functioN (cost)
  * `grad_f`: a gradient function, that either returns a vector of the subgradients or is a vector of gradients
  * `p`:      an initial value $p_0 ∈ \mathcal M$

you can also pass a [`ManifoldAlternatingGradientObjective`](@ref) `ago` containing `f` and `grad_f` instead.

for all optional parameters, see [`alternating_gradient_descent`](@ref).
