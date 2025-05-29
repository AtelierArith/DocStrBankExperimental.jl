```
ProjectToSO3(mat)
```

matをSO(3)に射影します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> ProjectToSO3([0.675 0.150  0.720; 0.370 0.771 -0.511; -0.630 0.619  0.472])
3×3 Matrix{Float64}:
  0.679011  0.148945   0.718859
  0.373207  0.773196  -0.512723
 -0.632187  0.616428   0.469421
```
