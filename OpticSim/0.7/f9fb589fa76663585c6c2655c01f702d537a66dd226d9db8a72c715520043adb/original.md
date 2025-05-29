```
Plane{T,N} <: ParametricSurface{T,N}
```

Infinite planar surface where the positive normal side is outside the surface.

By default this will not create any geometry for visualization, the optional `vishalfsizeu` and `vishalfsizev` arguments can be used to draw the plane as a rectangle for visualization **note that this does not fully represent the surface**. In this case, the rotation of the rectangle around the normal to the plane is defined by `visvec` - `surfacenormal×visvec` is taken as the vector along the u axis.

```julia
Plane(surfacenormal::SVector{N,T}, pointonplane::SVector{N,T}; interface::NullOrFresnel{T} = nullinterface(T), vishalfsizeu::T = 0.0, vishalfsizev::T = 0.0, visvec::SVector{N,T} = [0.0, 1.0, 0.0])
Plane(nx::T, ny::T, nz::T, x::T, y::T, z::T; interface::NullOrFresnel{T} = nullinterface(T), vishalfsizeu::T = 0.0, vishalfsizev::T = 0.0, visvec::SVector{N,T} = [0.0, 1.0, 0.0])
```
