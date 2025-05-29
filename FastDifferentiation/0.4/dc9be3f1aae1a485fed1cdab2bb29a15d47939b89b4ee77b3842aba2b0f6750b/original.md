make*variables(name::Symbol,array*size::T...)

Returns an Array of variables with names corresponding to their indices in the Array. 

## Example:

```julia
julia> make_variables(:x,3)
3-element Vector{FastDifferentiation.Node}:
 x1
 x2
 x3

julia> make_variables(:x,2,3)
2×3 Matrix{FastDifferentiation.Node}:
 x1_1  x1_2  x1_3
 x2_1  x2_2  x2_3

julia> make_variables(:x,2,3,2)
2×3×2 Array{FastDifferentiation.Node, 3}:
[:, :, 1] =
 x1_1_1  x1_2_1  x1_3_1
 x2_1_1  x2_2_1  x2_3_1

[:, :, 2] =
 x1_1_2  x1_2_2  x1_3_2
 x2_1_2  x2_2_2  x2_3_2
```

```

```
