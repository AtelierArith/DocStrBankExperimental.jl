```
DefaultOrthogonalBasis{𝔽,VST<:VectorSpaceType}
```

An arbitrary orthogonal basis of vector space of type `VST` on a manifold. This will usually be the fastest orthogonal basis available for a manifold.

The type parameter `𝔽` denotes the [`AbstractNumbers`](@ref) that will be used as coefficients in linear combinations of the basis vectors.

# See also

[`VectorSpaceType`](@ref)
