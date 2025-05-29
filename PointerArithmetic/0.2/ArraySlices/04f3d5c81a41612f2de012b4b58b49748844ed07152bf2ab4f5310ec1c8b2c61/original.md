```
shift_start(sl::AbstractArray, i::Integer)
```

Shifts the array starting point in a certain number of items. Can be called using `<<` Usage:

```julia-repl
julia> arr = [1,2,3,4]
julia> sl = ArraySlice(arr, 2:3)
2-element Vector{Int64}:
2
3
julia> sl << 1
1-element Vector{Int64}:
3
julia> sl << -1
3-element Vector{Int64}:
1
2
3
```
