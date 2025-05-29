```
approx(x, y, xout; rule=2)
```

Approximate the value of a function at a given point using linear interpolation.

> `DateTime` is also supported. But `Date` not!


# Arguments

  * `x::AbstractVector{Tx}`: The x-coordinates of the data points.
  * `y::AbstractVector{Ty}`: The y-coordinates of the data points.
  * `xout::AbstractVector`: The x-coordinates of the points to approximate.
  * `rule::Int=2`: The interpolation rule to use. Default is 2.

      * 1: NaN
      * 2: nearest constant extrapolation
      * 3: linear extrapolation
