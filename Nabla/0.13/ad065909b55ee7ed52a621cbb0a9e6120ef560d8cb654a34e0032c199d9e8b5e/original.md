```
domain1{T}(in_domain::Function, measure::Function, points::Vector{T})
domain1(f::Function)
```

Attempt to find a domain for a unary, scalar function `f`.

# Arguments

  * `in_domain::Function`: Function that takes a single argument `x` and returns whether `x`   argument is in `f`'s domain.
  * `measure::Function`: Function that measures the size of a set of points for `f`.
  * `points::Vector{T}`: Ordered set of test points to construct the domain from.
