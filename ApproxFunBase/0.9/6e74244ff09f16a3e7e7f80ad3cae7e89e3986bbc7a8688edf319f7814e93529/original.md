```
points(s::Space,n::Integer)
```

Return a grid of approximately `n` points, for which a transform exists from values at the grid to coefficients in the space `s`.

# Examples

```jldoctest
julia> chebypts(n) = [cos((2i+1)pi/2n) for i in 0:n-1];

julia> points(Chebyshev(), 4) ≈ chebypts(4)
true
```
