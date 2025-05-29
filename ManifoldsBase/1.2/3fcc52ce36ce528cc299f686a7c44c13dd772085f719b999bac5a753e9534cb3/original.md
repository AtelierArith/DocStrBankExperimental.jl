```
TangentSpace{𝔽,M} = Fiber{𝔽,TangentSpaceType,M} where {𝔽,M<:AbstractManifold}
```

A manifold for the tangent space $T_p\mathcal M$ at a point $p\in\mathcal M$. This is modelled as an alias for [`VectorSpaceFiber`](@ref) corresponding to [`TangentSpaceType`](@ref).

# Constructor

```
TangentSpace(M::AbstractManifold, p)
```

Return the manifold (vector space) representing the tangent space $T_p\mathcal M$ at point `p`, $p\in\mathcal M$.
