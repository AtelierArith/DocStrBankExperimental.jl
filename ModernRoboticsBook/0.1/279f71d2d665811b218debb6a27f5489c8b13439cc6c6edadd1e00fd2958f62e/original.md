```
TransToRp(T)
```

Converts a homogeneous transformation matrix into a rotation matrix and position vector.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TransToRp([1 0 0 0; 0 0 -1 0; 0 1 0 3; 0 0 0 1])
([1 0 0; 0 0 -1; 0 1 0], [0, 0, 3])
```
