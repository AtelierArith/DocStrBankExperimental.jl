```
struct ConstantCartesianCoriolis{FT} <: AbstractRotation
```

A Coriolis implementation that accounts for the locally vertical and possibly both local horizontal components of a constant rotation vector. This is a more general implementation of [`FPlane`](@ref), which only accounts for the locally vertical component.
