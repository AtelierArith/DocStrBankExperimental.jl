```
(s::Space)(n::Integer, points...)
```

Evaluate `Fun(s, [zeros(n); 1])(points...)` efficiently without allocating the vector of coefficients.

# Examples

```jldoctest
julia> Chebyshev()(1, 0.5)
0.5
```
