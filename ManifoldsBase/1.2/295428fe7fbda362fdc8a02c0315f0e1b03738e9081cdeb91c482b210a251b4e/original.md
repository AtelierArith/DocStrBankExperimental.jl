```
DefaultOrthonormalBasis(𝔽::AbstractNumbers = ℝ, vs::VectorSpaceType = TangentSpaceType())
```

An arbitrary orthonormal basis of vector space of type `VST` on a manifold. This will usually be the fastest orthonormal basis available for a manifold.

The type parameter `𝔽` denotes the [`AbstractNumbers`](@ref) that will be used as coefficients in linear combinations of the basis vectors.

# See also

[`VectorSpaceType`](@ref)
