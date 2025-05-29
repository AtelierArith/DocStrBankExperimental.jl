```
PowerLieGroup(G::LieGroup, args...; kwargs...)
(G::LieGroup)^(n::Integer) = PowerLieGroup(G, n)
```

Generate the [`LieGroup`](@ref) of the `n`-th power of a Lie group `G` or manifold `M`. If passed a Lie group `G`, the group operation on the [`PowerLieGroup`](@ref) is the same as on `G`, but applied elementwise. Internally, the corresponding [`PowerGroupOperation`](@ref) is created. If you pass a manifold `M`, you have to provide the corresponding [`PowerGroupOperation`](@ref) yourself.

Bot the arguments `args...` as well as the keyword arguments `kwargs...` are passed on to the constructor of the [`PowerManifold`](@extref `ManifoldsBase.PowerManifold`). This especially includes the `size` of the manifold and allows to specify a [`NestedPowerRepresentation`](@extref `ManifoldsBase.NestedPowerRepresentation`).
