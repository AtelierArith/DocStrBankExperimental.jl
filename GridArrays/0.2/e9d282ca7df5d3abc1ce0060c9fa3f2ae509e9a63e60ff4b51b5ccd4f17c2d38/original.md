```
struct ChebyshevExtremae{T} <: AbstractIntervalGrid{T}
```

A grid with chebyshev extrema on [-1,1].

# Example

```jldocs
julia> ChebyshevExtremae(4)
4-element ChebyshevExtremae{Float64}:
  1.0
  0.5000000000000001
 -0.4999999999999998
 -1.0
```
