```
Sphere{T,N} <: ParametricSurface{T,N}
```

原点を中心とした球面。

```julia
Sphere(radius::T = 1.0; interface::NullOrFresnel{T} = nullinterface(T))
```
