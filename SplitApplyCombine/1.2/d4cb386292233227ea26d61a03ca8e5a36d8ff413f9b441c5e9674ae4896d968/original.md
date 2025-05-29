```
filterview(f, a)
```

Return a view of an array `a` without elements for which `f` is `false`. Similar to `filter(f, a)`, except returns a view instead of a copy. Filtered indices are computed once, and are not updated when the array gets modified.

# Example

```
julia> a = [1, 2, 3];

julia> b = filterview(isodd, a)
2-element view(::Vector{Int64}, [1, 3]) with eltype Int64:
 1
 3

julia> b[2] = 10;

julia> a
3-element Vector{Int64}:
  1
  2
 10

julia> b
2-element view(::Vector{Int64}, [1, 3]) with eltype Int64:
  1
 10
```
