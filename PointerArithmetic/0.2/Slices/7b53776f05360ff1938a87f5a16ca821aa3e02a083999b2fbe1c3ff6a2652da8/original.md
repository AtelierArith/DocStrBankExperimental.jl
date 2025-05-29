```
shift_start(sl::Slice, i::Integer)
```

Shifts the array starting point in a certain number of items. Can be called using `<<` Usage:

```julia-repl
julia> arr = [1,2,3,4]
julia> sl = Slice(arr, 2:3)
2-element Slice{Int64}:
2
3
julia> sl << 1
1-element Slice{Int64}:
3
julia> sl << -1
3-element Slice{Int64}:
1
2
3
```
