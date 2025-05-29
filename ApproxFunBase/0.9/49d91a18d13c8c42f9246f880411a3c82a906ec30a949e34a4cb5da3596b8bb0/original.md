```
points(f::Fun)
```

Return a grid of points that `f` can be transformed into values and back.

# Examples

```jldoctest
julia> f = Fun(x->x^2);

julia> chebypts(n) = [cos((2i+1)pi/2n) for i in 0:n-1];

julia> points(f) ≈ chebypts(ncoefficients(f))
true
```
