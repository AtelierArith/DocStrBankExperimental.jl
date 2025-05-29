```
get_preconditioner(M::AbstractManifold, mho::ManifoldHessianObjective, p, X)
```

evaluate the symmetric, positive definite preconditioner (approximation of the inverse of the Hessian of the cost function `F`) of a [`ManifoldHessianObjective`](@ref) `mho` at the point `p` applied to a tangent vector `X`.
