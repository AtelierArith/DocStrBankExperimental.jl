```
so3ToVec(so3mat)
```

Converts an so(3) representation to a 3-vector.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> so3ToVec([0 -3 2; 3 0 -1; -2 1 0])
3-element Vector{Int64}:
 1
 2
 3
```
