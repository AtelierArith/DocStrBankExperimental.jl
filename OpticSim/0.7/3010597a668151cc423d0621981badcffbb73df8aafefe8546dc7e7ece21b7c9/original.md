```
makemesh(object, subdivisions::Int = 30) -> TriangleMesh
```

Creates a [`TriangleMesh`](@ref) from an object, either a [`ParametricSurface`](@ref), [`CSGTree`](@ref) or certain surfaces (e.g. `Circle`, `Rectangle`). This is used for visualization purposes only.
