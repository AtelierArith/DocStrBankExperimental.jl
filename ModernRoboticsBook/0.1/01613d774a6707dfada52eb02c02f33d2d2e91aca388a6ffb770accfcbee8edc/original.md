```
ProjectToSE3(mat)
```

Returns a projection of mat into SE(3).

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> ProjectToSE3([0.675 0.150 0.720 1.2; 0.370 0.771 -0.511 5.4; -0.630 0.619 0.472 3.6; 0.003 0.002 0.010 0.9])
4×4 Matrix{Float64}:
  0.679011  0.148945   0.718859  1.2
  0.373207  0.773196  -0.512723  5.4
 -0.632187  0.616428   0.469421  3.6
  0.0       0.0        0.0       1.0
```
