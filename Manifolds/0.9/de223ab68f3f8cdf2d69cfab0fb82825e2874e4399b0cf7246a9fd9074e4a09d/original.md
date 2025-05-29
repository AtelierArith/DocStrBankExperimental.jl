```
Identity{O<:AbstractGroupOperation}
```

Represent the group identity element $e ∈ \mathcal{G}$ on a Lie group $\mathcal G$ with [`AbstractGroupOperation`](@ref) of type `O`.

Similar to the philosophy that points are agnostic of their group at hand, the identity does not store the group `g` it belongs to. However it depends on the type of the [`AbstractGroupOperation`](@ref) used.

See also [`identity_element`](@ref) on how to obtain the corresponding [`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`) or array representation.

# Constructors

```
Identity(G::AbstractDecoratorManifold{𝔽})
Identity(o::O)
Identity(::Type{O})
```

create the identity of the corresponding subtype `O<:`[`AbstractGroupOperation`](@ref)
