```
gridmake(arrays::Union{AbstractVector,AbstractMatrix}...)
```

Expand one or more vectors (or matrices) into a matrix where rows span the cartesian product of combinations of the input arrays. Each column of the input arrays will correspond to one column of the output matrix. The first array varies the fastest (see example)

# Example

```jlcon
julia> x = [1, 2, 3]; y = [10, 20]; z = [100, 200];

julia> gridmake(x, y, z)
12×3 Matrix{Int64}:
 1  10  100
 2  10  100
 3  10  100
 1  20  100
 2  20  100
 3  20  100
 1  10  200
 2  10  200
 3  10  200
 1  20  200
 2  20  200
 3  20  200
```
