```
curve_length(f::Function, a::Real, b::Real) -> Float64
```

Calculates the length of the curve given by `f`, where `f` is function of one parameter, on interval <`a`, `b`> of said parameter.

# Arguments

  * `f::Function`: function of the curve to be measured,
  * `a::Real`: left-bound of the interval to be integrated on,
  * `b::Real`: right-bound of the interval to be integrated on,

# Keywords

# Returns

  * `Float64`: length of the curve defined by the `f` on the interval <`a`, `b`>.

# Throws
