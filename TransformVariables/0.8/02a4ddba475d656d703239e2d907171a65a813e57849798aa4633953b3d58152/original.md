```
as(tuple)
as(namedtuple)
```

Return a transformation that transforms consecutive groups of real numbers to a (named) tuple, using the given transformations.

```jldoctest
julia> t = as((asℝ₊, UnitVector(3)));

julia> dimension(t)
3

julia> transform(t, zeros(dimension(t)))
(1.0, [0.0, 0.0, 1.0])

julia> t2 = as((σ = asℝ₊, u = UnitVector(3)));

julia> dimension(t2)
3

julia> transform(t2, zeros(dimension(t2)))
(σ = 1.0, u = [0.0, 0.0, 1.0])
```
