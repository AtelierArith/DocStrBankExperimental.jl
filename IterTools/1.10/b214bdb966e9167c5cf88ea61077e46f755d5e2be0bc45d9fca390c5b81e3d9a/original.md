```
ivec(iter)
```

Drops all shape from `iter` while iterating. Like a non-materializing version of [`vec`](https://docs.julialang.org/en/stable/base/arrays/#Base.vec).

```jldoctest
julia> m = collect(reshape(1:6, 2, 3))
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> collect(ivec(m))
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
