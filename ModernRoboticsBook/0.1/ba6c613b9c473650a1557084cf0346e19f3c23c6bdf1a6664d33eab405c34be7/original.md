```
ScrewToAxis(q, s, h)
```

Takes a parametric description of a screw axis and converts it to a normalized screw axis.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> ScrewToAxis([3; 0; 0], [0; 0; 1], 2)
6-element Vector{Int64}:
  0
  0
  1
  0
 -3
  2
```
