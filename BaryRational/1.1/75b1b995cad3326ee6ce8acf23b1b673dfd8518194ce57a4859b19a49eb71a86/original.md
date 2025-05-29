```
bary(z, f, x, w)
```

evaluate f(z)

# Arguments

  * z::Z                 : the point at which to evaluate f
  * f::AbstractVector{F} : vector of function values at x
  * x::AbstractVector{X} : vector of eval locations of f (sorted)
  * w::AbstractVector{W} : weights for locations x
