```
project(M::Hyperbolic, p, X)
```

Perform an orthogonal projection with respect to the Minkowski inner product of `X` onto the tangent space at `p` of the [`Hyperbolic`](@ref) space `M`.

The formula reads

$$
Y = X + ⟨p,X⟩_{\mathrm{M}} p,
$$

where $⟨⋅, ⋅⟩_{\mathrm{M}}$ denotes the [`MinkowskiMetric`](@ref) on the embedding, the [`Lorentz`](@ref)ian manifold.

!!! note
    Projection is only available for the (default) [`HyperboloidTVector`](@ref) representation, the others don't have such an embedding

