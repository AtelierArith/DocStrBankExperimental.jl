```
Sphere{T,N} <: ParametricSurface{T,N}
```

Spherical surface centered at the origin.

```julia
Sphere(radius::T = 1.0; interface::NullOrFresnel{T} = nullinterface(T))
```
