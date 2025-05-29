```
XReflection()
```

Construct a reflection about the x-axis (y-coordinate changes sign).

Example:

```jldoctest
julia> trans = XReflection()
LinearMap([1 0; 0 -1])

julia> trans(Point(1, 1))
2-element Point{Int64} with indices SOneTo(2):
  1
 -1
```
