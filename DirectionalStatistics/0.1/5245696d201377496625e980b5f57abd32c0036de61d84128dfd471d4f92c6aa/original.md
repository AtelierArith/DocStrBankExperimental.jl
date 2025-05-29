Geometric median of a collection of points. Points can be specified as real numbers (1d), complex numbers (2d), or arbitrary vectors.

See [https://en.wikipedia.org/wiki/Geometric_median].

```jldoctest
julia> geometric_median([1, 2, 3])
2.0

julia> geometric_median([0, 1, 1im, 1+1im]) ≈ 0.5+0.5im
true

julia> geometric_median([[0, 0], [0, 1], [1, 0], [1, 1]]) ≈ [0.5, 0.5]
true
```
