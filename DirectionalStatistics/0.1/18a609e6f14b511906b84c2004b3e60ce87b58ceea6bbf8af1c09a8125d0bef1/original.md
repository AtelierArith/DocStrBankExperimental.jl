Select a pair of most distant points in the collection. Points can be specified as real numbers (1d), complex numbers (2d), or arbitrary vectors.

```jldoctest
julia> most_distant_points([1, 2, 3])
(3, 1)

julia> most_distant_points([0, 1, 1+1im])
(1 + 1im, 0 + 0im)

julia> most_distant_points([[0, 0], [0, 1], [1, 1]])
([1, 1], [0, 0])
```
