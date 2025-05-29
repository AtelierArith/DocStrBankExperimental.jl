```
TangentDiffBackend <: AbstractRiemannianDiffBackend
```

A backend that uses tangent spaces and bases therein to derive an intrinsic differentiation scheme.

Since it works in tangent spaces at argument and function value, methods might require a retraction and an inverse retraction as well as a basis.

In the tangent space itself, this backend then employs a (Euclidean) backend.

# Constructor

```
TangentDiffBackend(diff_backend)
```

where `diff_backend` is a (Euclidean) backend to be used on the tangent space.

With the keyword arguments

  * `retraction` an [AbstractRetractionMethod](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/retractions.html) (`ExponentialRetraction` by default)
  * `inverse_retraction` an [AbstractInverseRetractionMethod](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/retractions.html) `LogarithmicInverseRetraction` by default)
  * `basis_arg` an [AbstractBasis](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/bases.html) (`DefaultOrthogonalBasis` by default)
  * `basis_val` an [AbstractBasis](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/bases.html) (`DefaultOrthogonalBasis` by default)
