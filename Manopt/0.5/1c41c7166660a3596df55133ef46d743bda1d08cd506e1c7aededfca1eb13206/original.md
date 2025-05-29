```
PreconditionedDirection(preconditioner; kwargs...)
PreconditionedDirection(M::AbstractManifold, preconditioner; kwargs...)
```

Add a preconditioner to a gradient processor following the [motivation for optimization](https://en.wikipedia.org/wiki/Preconditioner#Preconditioning_in_optimization), as a linear invertible map $P: T_{p}\mathcal M → T_{p}\mathcal M$ that usually should be

  * symmetric: $⟨X, P(Y)⟩ = ⟨P(X), Y⟩$
  * positive definite $⟨X, P(X)⟩ > 0$ for $X$ not the zero-vector

The gradient is then preconditioned as $P(X)$, where $X$ is either the gradient of the objective or the result of a previous (internally stored) gradient processor.

For example if you provide as the preconditioner the inverse of the Hessian $\operatorname{Hess}^{-1} f$, you turn a gradient descent into a Newton method.

# Arguments

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$ (optional)
  * `preconditioner`:   preconditioner function, either as a `(M, p, X) -> Y` allocating or `(M, Y, p, X) -> Y` mutating function

# Keyword arguments

  * `direction=`[`IdentityUpdateRule`](@ref) internal [`DirectionUpdateRule`](@ref) to determine the gradients to store or a [`ManifoldDefaultsFactory`](@ref) generating one
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`PreconditionedDirectionRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

