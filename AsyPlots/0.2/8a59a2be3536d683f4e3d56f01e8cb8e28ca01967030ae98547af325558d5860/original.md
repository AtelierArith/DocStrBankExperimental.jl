```
Point(x::Real,y::Real;kwargs...)
Point(x::Real,y::Real,z::Real;kwargs...)
Point(P;kwargs...)
```

Return a Point2D or Point3D object, as appropriate

# Examples

```julia-repl
julia> Point(1,2;pen=Pen(opacity=0.5),shape=:plus)
Point2D(1,2;pen=opacity(0.5))
```
