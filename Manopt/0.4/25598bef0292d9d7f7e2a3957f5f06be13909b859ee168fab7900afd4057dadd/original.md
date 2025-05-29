```
get_preconditioner(amp::AbstractManoptProblem, p, X)
```

evaluate the symmetric, positive definite preconditioner (approximation of the inverse of the Hessian of the cost function `f`) of a [`AbstractManoptProblem`](@ref) `amp`s objective at the point `p` applied to a tangent vector `X`.
