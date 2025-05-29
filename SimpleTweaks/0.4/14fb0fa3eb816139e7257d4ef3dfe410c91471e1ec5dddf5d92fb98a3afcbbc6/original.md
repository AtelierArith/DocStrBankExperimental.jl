```
quadrature(f::Function, a::Real, b::Real) -> Float64
```

Calculates definite integral of the function `f` in interval <`a`, `b`> using the Gaussian three point quadrature rule.

# Arguments

  * `f::Function`: function to be integrated,
  * `a::Real`: left-bound of the interval to be integrated on,
  * `b::Real`: right-bound of the interval to be integrated on,

# Keywords

# Returns

  * `Float64`: definite integral of the function `f` on interval <`a`, `b`>.

# Throws
