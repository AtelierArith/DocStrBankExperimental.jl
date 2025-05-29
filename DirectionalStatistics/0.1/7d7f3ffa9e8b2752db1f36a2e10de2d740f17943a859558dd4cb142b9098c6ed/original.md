Select indices of a pair of most distant points in the collection. Points can be specified as real numbers (1d), complex numbers (2d), or arbitrary vectors.

```jldoctest
julia> most_distant_points_ix([1, 2, 3])
(3, 1)

julia> most_distant_points_ix([0, 1, 1+1im])
(3, 1)

julia> most_distant_points_ix([[0, 0], [0, 1], [1, 1]])
(3, 1)
```
