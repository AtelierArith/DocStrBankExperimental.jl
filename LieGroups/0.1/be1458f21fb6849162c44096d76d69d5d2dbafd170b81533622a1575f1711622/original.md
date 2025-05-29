```
AbstractLieGroup{𝔽, O<:AbstractGroupOperation, M<:AbstractManifold{𝔽}} <: AbstractManifold{𝔽}
```

An abstract type to represent Lie groups. For most cases it should suffice to “combine” an [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) with an [`AbstractGroupOperation`](@ref), see [`LieGroup`](@ref).
