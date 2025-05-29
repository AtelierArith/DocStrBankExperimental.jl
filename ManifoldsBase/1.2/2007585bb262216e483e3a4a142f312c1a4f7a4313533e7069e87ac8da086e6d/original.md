```
DiagonalizingOrthonormalBasis{𝔽,TV} <: AbstractOrthonormalBasis{𝔽,TangentSpaceType}
```

An orthonormal basis `Ξ` as a vector of tangent vectors (of length determined by [`manifold_dimension`](@ref)) in the tangent space that diagonalizes the curvature tensor $R(u,v)w$ and where the direction `frame_direction` $v$ has curvature `0`.

The type parameter `𝔽` denotes the [`AbstractNumbers`](@ref) that will be used as coefficients in linear combinations of the basis vectors.

# Constructor

```
DiagonalizingOrthonormalBasis(frame_direction, 𝔽::AbstractNumbers = ℝ)
```
