```
RpToTrans(R, p)
```

Converts a rotation matrix and a position vector into homogeneous transformation matrix.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> RpToTrans([1 0 0; 0 0 -1; 0 1 0], [1, 2, 5])
4×4 Matrix{Int64}:
 1  0   0  1
 0  0  -1  2
 0  1   0  5
 0  0   0  1
```
