```
Cylinder{T,N} <: ParametricSurface{T,N}
```

Cylinder of infinite height centered at the origin, oriented along the z-axis. `visheight` is used for visualization purposes only, **note that this does not fully represent the surface**.

```julia
Cylinder(radius::T, visheight::T = 2.0; interface::NullOrFresnel{T} = nullinterface(T))
```
