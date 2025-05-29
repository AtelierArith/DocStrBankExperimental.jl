```
Ellipse{T<:AbstractFloat}  <: Obstacle{T}
```

Ellipse obstacle that also allows ray-splitting. The ellipse is always oriented on the x and y axis (although you can make whichever you want the major one).

### Fields:

  * `c::SVector{2,T}` : Center.
  * `a::T` : x semi-axis.
  * `b::T` : y semi-axis.
  * `pflag::Bool` : Flag that keeps track of where the particle is currently propagating. `true` (default) is associated with being outside the ellipse.
  * `name::String` : Some name given for user convenience. Defaults to `"Ellipse"`.

The ellipse equation is given by

$$
\left(\frac{x - c[1]}{a} \right)^2+ \left(\frac{y - c[2]}{b}\right)^2 = 1
$$
