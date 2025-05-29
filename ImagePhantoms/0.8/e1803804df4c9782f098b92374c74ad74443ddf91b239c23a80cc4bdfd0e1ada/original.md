```
Object{S, D, V, C, A, Da}(center, width, angle, value) <: AbstractObject
    where {S <: AbstractShape, V <: Number, C,A <: RealU}
```

General container for 2D and 3D objects for defining image phantoms.

  * `center::NTuple{D,C}` coordinates of "center" of this object
  * `width::NTuple{D,C}` "width" along each axis (e.g., FWHM for Gauss, radii for Ellipse)
  * `angle::NTuple{D-1,A}` angle of x' axis relative to x axis, in radians (or with units)
  * `value::V` "intensity" value for this object

# Example

```jldoctest
julia> Object(Ellipse(), (0,0), (1,2), 0.0, 1//2)
Object2d{Ellipse, Rational{Int64}, Int64, Float64, 1, Float64} (S, D, V, ...)
 center::NTuple{2,Int64} (0, 0)
 width::NTuple{2,Int64} (1, 2)
 angle::Tuple{Float64} (0.0,)
 value::Rational{Int64} 1//2
```
