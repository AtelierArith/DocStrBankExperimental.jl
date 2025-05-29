```
Identity{O<:AbstractGroupOperation}
```

Represent the group identity element $e ∈ \mathcal G$ on an [`AbstractLieGroup`](@ref) $\mathcal G$ with [`AbstractGroupOperation`](@ref) of type `O`.

Similar to the philosophy that points are agnostic of their group at hand, the identity does not store the group $\mathcal G$ it belongs to. However it depends on the type of the [`AbstractGroupOperation`](@ref) used.

See also [`identity_element`](@ref) on how to obtain the corresponding [`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`) or array representation.

# Constructors

```
Identity(::AbstractLieGroup{𝔽,O}) where {𝔽,O<:AbstractGroupOperation}
Identity(o::AbstractGroupOperation)
Identity(::Type{AbstractGroupOperation})
```

create the identity of the corresponding subtype `O<:`[`AbstractGroupOperation`](@ref)
