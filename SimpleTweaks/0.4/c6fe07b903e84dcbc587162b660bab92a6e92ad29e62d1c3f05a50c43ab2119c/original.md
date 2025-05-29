```
curve_fraction(f::Function,a::Real,b::Real,r::Real) -> Float64
```

Retunrs the position of the fraction of the length from the interval <`a`, `b`>, where the length of the curve is given by one parameter function `f`.

# Arguments

  * `f::Function`: function of the curve,
  * `a::Real`: left-bound of the interval to be integrated on,
  * `b::Real`: right-bound of the interval to be integrated on,
  * `r::Real`: fraction of the length of the curve given by `f` from the left,

# Keywords

# Returns

  * `Float64`: position of the fraction of the length from the interval <`a`, `b`>.

# Throws
