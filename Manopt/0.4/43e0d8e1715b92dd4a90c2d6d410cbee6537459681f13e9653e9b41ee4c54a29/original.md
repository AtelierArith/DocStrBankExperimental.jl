```
stochastic_gradient_descent!(M, grad_f, p)
stochastic_gradient_descent!(M, msgo, p)
```

perform a stochastic gradient descent in place of `p`.

# Input

  * `M`:      a manifold $\mathcal M$
  * `grad_f`: a gradient function, that either returns a vector of the subgradients or is a vector of gradients
  * `p`:      an initial value $p ∈ \mathcal M$

Alternatively to the gradient you can provide an [`ManifoldStochasticGradientObjective`](@ref) `msgo`, then using the `cost=` keyword does not have any effect since if so, the cost is already within the objective.

for all optional parameters, see [`stochastic_gradient_descent`](@ref).
