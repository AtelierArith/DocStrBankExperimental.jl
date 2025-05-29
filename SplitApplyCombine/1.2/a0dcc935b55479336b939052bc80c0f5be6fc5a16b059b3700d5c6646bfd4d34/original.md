```
invert(a)
```

Return a new nested container by reversing the order of the nested container `a`, for example turning a dictionary of arrays into an array of dictionaries, such that  `a[i][j] === invert(a)[j][i]`.

Note that in order for the keys of the inner and outer structure to be known, the input container `a` must not be empty. 

# Examples

```julia
julia> invert([[1,2,3],[4,5,6]])
3-element Array{Array{Int64,1},1}:
 [1, 4]
 [2, 5]
 [3, 6]

julia> invert((a = [1, 2, 3], b = [2.0, 4.0, 6.0]))
3-element Array{NamedTuple{(:a, :b),Tuple{Int64,Float64}},1}:
 (a = 1, b = 2.0)
 (a = 2, b = 4.0)
 (a = 3, b = 6.0)
```
