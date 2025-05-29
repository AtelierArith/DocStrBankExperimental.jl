```
GridSagSurface{T,N,S<:Union{ZernikeSurface{T,N},ChebyshevSurface{T,N}},Nu,Nv} <: ParametricSurface{T,N}
```

Either a Zernike (circular) or Chebyshev (rectangular) surface with grid sag height added to the base sag. The surface shape is determined by either a linear or a bicubic spline interpolation of the `Nu×Nv` grid of sag values, set by the `interpolation` argument taking either `GridSagLinear` or `GridSagBicubic`.

Each entry in the grid is a vector of the form $[z, \frac{\partial z}{\partial x}, \frac{\partial z}{\partial y}, \frac{\partial^2 z}{\partial x \partial y}]$. The first data item corresponds to the lower left corner of the surface, that is, the corner defined by the -u and -v limit. Each point that follows is read across the face of the surface from left to right moving upwards. If zero is given for the partials (and using bicubic interpolation) then the partials will be approximated using finite differences.

The sag grid can be decentered from the surface in uv space, if so the surface may become wild outside of the area over which the grid is defined. It is advised to clip the surface to the valid area using CSG operations in this case.

A surface can also be generated from a `.GRD` file by passing in the filename as the first and only positional argument. In this case the surface will be rectangular with optional radius and conic.

See docs for [`ZernikeSurface`](@ref) and [`ChebyshevSurface`](@ref) for details of the base surface.

```julia
GridSagSurface(basesurface::Union{ZernikeSurface{T,N},ChebyshevSurface{T,N}}, sag_grid::AbstractArray{T,3}; interpolation = GridSagBicubic, decenteruv = (0, 0))
GridSagSurface{T}(filename::String; radius = Inf, conic = 0, interpolation = GridSagBicubic)
```
