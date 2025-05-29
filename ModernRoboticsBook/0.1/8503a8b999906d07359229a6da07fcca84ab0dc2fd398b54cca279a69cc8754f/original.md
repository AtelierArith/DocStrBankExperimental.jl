```
ad(V)
```

Calculate the 6x6 matrix [adV] of the given 6-vector.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> ad([1, 2, 3, 4, 5, 6])
6×6 Matrix{Float64}:
  0.0  -3.0   2.0   0.0   0.0   0.0
  3.0   0.0  -1.0   0.0   0.0   0.0
 -2.0   1.0   0.0   0.0   0.0   0.0
  0.0  -6.0   5.0   0.0  -3.0   2.0
  6.0   0.0  -4.0   3.0   0.0  -1.0
 -5.0   4.0   0.0  -2.0   1.0   0.0
```
