```
VecTose3(V)
```

Converts a spatial velocity vector into a 4x4 matrix in se3.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> VecTose3([1 2 3 4 5 6])
4×4 Matrix{Float64}:
  0.0  -3.0   2.0  4.0
  3.0   0.0  -1.0  5.0
 -2.0   1.0   0.0  6.0
  0.0   0.0   0.0  0.0
```
