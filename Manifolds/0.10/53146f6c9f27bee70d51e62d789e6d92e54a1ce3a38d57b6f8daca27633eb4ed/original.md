```
compose(G::AbstractDecoratorManifold, p, q)
```

Compose elements $p,q ∈ \mathcal{G}$ using the group operation $p \circ q$.

For implementing composition on a new group manifold, please overload `_compose` instead so that methods with [`Identity`](@ref) arguments are not ambiguous.
