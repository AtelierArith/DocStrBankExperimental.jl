```
get_coordinates(M::Hyperbolic, p, X, ::DefaultOrthonormalBasis)
```

Compute the coordinates of the vector `X` with respect to the orthogonalized version of the unit vectors from $ℝ^n$, where $n$ is the manifold dimension of the [`Hyperbolic`](@ref)  `M`, putting them into the tangent space at `p` and orthonormalizing them.
