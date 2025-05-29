```
VecTose3(V)
```

空間速度ベクトルをse3の4x4行列に変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> VecTose3([1 2 3 4 5 6])
4×4 Matrix{Float64}:
  0.0  -3.0   2.0  4.0
  3.0   0.0  -1.0  5.0
 -2.0   1.0   0.0  6.0
  0.0   0.0   0.0  0.0
```
