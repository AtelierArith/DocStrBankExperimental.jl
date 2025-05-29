```
is_point(𝔤::LieAlgebra, X; kwargs...)
```

Check whether `X` is a valid point on the Lie Algebra `𝔤`. This falls back to checking whether `X` is a valid point on the tangent space at the [`identity_element`](@ref)`(G)` on the [`base_manifold`](@ref)`(G)` on the [`AbstractLieGroup`](@ref) of `𝔤`
