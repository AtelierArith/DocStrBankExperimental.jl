```
BSplineSurface{P,S,N,M} <: SplineSurface{P,S,N,M}
```

Curve order is the same in the u and v direction and fixed over all spans. u and v knot vectors are allowed to be different - *may change this to make them both the same*.

Control points in the u direction correspond to columns, with the lowest value of u corresponding to row 1. Control points in the v direction correspond to rows, with the lowest value of v corresponding to col 1.

!!! danger
    This surface does not create a valid half-space, requires updates to function correctly.


```julia
BSplineSurface{P,S,N,M}(knots::KnotVector{S}, controlpoints::AbstractArray{<:AbstractArray{S,1},2})
BSplineSurface{P,S,N,M}(uknots::KnotVector{S}, vknots::KnotVector{S}, controlpoints::AbstractArray{<:AbstractArray{S,1},2})
```
