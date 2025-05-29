```
Point(x::Real,y::Real;kwargs...)
Point(x::Real,y::Real,z::Real;kwargs...)
Point(P;kwargs...)
```

適切に Point2D または Point3D オブジェクトを返します

# 例

```julia-repl
julia> Point(1,2;pen=Pen(opacity=0.5),shape=:plus)
Point2D(1,2;pen=opacity(0.5))
```
