```
WrapperSurface{T,S<:Surface{T}} <: Surface{T}
```

A generic surface type which serves as a basis for extension of [`Surface`](@ref)s for custom [`OpticalInterface`](@ref) subclasses. Essentially just forwards all `Surface` and `ParametricSurface` methods to a field of the `WrapperSurface` named `surface`. Also provides a generic implementation of [`surfaceintersection`](@ref) which tests for an intersection with the underlying surface and returns either an [`EmptyInterval`](@ref) or a half space (never a closed interval).
