```
hat(M::AbstractDecoratorManifold{𝔽,O}, ::Identity{O}, Xⁱ) where {𝔽,O<:AbstractGroupOperation}
```

Given a basis $e_i$ on the tangent space at a the [`Identity`](@ref) and tangent component vector $X^i$, compute the equivalent vector representation ``X=X^i e_i**, where Einstein summation notation is used:

$$
∧ : X^i ↦ X^i e_i
$$

For array manifolds, this converts a vector representation of the tangent vector to an array representation. The [`vee`](@ref) map is the `hat` map's inverse.
