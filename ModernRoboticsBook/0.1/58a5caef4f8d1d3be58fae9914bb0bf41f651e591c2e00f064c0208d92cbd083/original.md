```
AxisAng6(expc6)
```

Converts a 6-vector of exponential coordinates into screw axis-angle form.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> AxisAng6([1, 0, 0, 1, 2, 3])
([1.0, 0.0, 0.0, 1.0, 2.0, 3.0], 1.0)
```
