```
NonlinearLeastSquaresObjective{T<:AbstractEvaluationType} <: AbstractManifoldObjective{T}
```

A type for nonlinear least squares problems. `T` is a [`AbstractEvaluationType`](@ref) for the `F` and Jacobian functions.

Specify a nonlinear least squares problem

# Fields

  * `f`                      a function $f: \mathcal M → ℝ^d$ to minimize
  * `jacobian!!`             Jacobian of the function $f$
  * `jacobian_tangent_basis` the basis of tangent space used for computing the Jacobian.
  * `num_components`         number of values returned by `f` (equal to `d`).

Depending on the [`AbstractEvaluationType`](@ref) `T` the function $F$ has to be provided:

  * as a functions `(M::AbstractManifold, p) -> v` that allocates memory for `v` itself for an [`AllocatingEvaluation`](@ref),
  * as a function `(M::AbstractManifold, v, p) -> v` that works in place of `v` for a [`InplaceEvaluation`](@ref).

Also the Jacobian $jacF!!$ is required:

  * as a functions `(M::AbstractManifold, p; basis_domain::AbstractBasis) -> v` that allocates memory for `v` itself for an [`AllocatingEvaluation`](@ref),
  * as a function `(M::AbstractManifold, v, p; basis_domain::AbstractBasis) -> v` that works in place of `v` for an [`InplaceEvaluation`](@ref).

# Constructors

```
NonlinearLeastSquaresProblem(M, F, jacF, num_components; evaluation=AllocatingEvaluation(), jacobian_tangent_basis=DefaultOrthonormalBasis())
```

# See also

[`LevenbergMarquardt`](@ref), [`LevenbergMarquardtState`](@ref)
