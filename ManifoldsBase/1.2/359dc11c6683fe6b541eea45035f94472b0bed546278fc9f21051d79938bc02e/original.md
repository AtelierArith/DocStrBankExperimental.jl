```
ProjectedOrthonormalBasis(method::Symbol, 𝔽::AbstractNumbers = ℝ)
```

An orthonormal basis that comes from orthonormalization of basis vectors of the ambient space projected onto the subspace representing the tangent space at a given point.

The type parameter `𝔽` denotes the [`AbstractNumbers`](@ref) that will be used as coefficients in linear combinations of the basis vectors.

Available methods:

  * `:gram_schmidt` uses a modified Gram-Schmidt orthonormalization.
  * `:svd` uses SVD decomposition to orthogonalize projected vectors. The SVD-based method should be more numerically stable at the cost of an additional assumption (local metric tensor at a point where the basis is calculated has to be diagonal).
