```
CotangentSpace{𝔽,M} = Fiber{𝔽,CotangentSpaceType,M} where {𝔽,M<:AbstractManifold}
```

A manifold for the Cotangent space $T^*_p\mathcal M$ at a point $p\in\mathcal M$. This is modelled as an alias for [`VectorSpaceFiber`](@ref) corresponding to [`CotangentSpaceType`](@ref).

# Constructor

```
CotangentSpace(M::AbstractManifold, p)
```

Return the manifold (vector space) representing the cotangent space $T^*_p\mathcal M$ at point `p`, $p\in\mathcal M$.
