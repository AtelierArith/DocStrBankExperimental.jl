```
mapview(f, a)
```

Return a view of `a` where each element is mapped through function `f`. The iteration and indexing properties of `a` are preserved. Similar to `map(f, a)`, except evaluated lazily.

# Example

```julia
julia> a = [1,2,3];

julia> b = mapview(-, a)
3-element MappedArray{Int64,1,typeof(-),Array{Int64,1}}:
 -1
 -2
 -3

julia> a[1] = 10;

julia> b
3-element MappedArray{Int64,1,typeof(-),Array{Int64,1}}:
 -10
  -2
  -3
```
