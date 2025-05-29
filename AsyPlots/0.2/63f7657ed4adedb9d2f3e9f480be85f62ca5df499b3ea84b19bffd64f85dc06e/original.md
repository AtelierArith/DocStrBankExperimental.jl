```
Point3D(x::Real,y::Real,z::Real; label="",pen=Pen())
Point3D(P; label="",pen=Pen())
```

A graphics primitive representing a three-dimensional point.

`P` may be a 3-tuple of real numbers or a `Vec3`

# Examples

```julia-repl
julia> Point3D(0,4,5;pen="DarkGreen")
```
