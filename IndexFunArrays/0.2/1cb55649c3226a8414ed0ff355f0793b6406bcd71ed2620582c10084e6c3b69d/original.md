```
selectsizes(x::AbstractArray, dim; keep_dims=true)
```

Additional size method to access the size at several dimensions in one call. `keep_dims` allows to return the other dimensions as singletons.

# Examples

```jldoctest
julia> x = ones((2,4,6,8, 10));

julia> selectsizes(x, (2,3))
(1, 4, 6, 1, 1)

julia> selectsizes(x, 5)
(1, 1, 1, 1, 10)

julia> selectsizes(x, (5,))
(1, 1, 1, 1, 10)

julia> selectsizes(x, (2,3,4), keep_dims=false)
(4, 6, 8)

julia> selectsizes(x, (4,3,2), keep_dims=false)
(8, 6, 4)
```
