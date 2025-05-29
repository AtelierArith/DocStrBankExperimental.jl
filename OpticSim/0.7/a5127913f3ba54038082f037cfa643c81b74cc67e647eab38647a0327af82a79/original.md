```
BezierSurface{P,S,N,M} <: SplineSurface{P,S,N,M}
```

Bezier surface defined by grid of control points.

!!! danger
    This surface does not create a valid half-space, requires updates to function correctly.


```julia
BezierSurface{P,S,N,M}(controlpoints::AbstractArray{<:AbstractArray{S,1},2})
```
