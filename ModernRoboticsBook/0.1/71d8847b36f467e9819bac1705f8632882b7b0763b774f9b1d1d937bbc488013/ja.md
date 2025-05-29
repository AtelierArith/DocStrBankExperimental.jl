```
MatrixLog3(R)
```

回転行列の行列対数を計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> MatrixLog3([0 0 1; 1 0 0; 0 1 0])
3×3 Matrix{Float64}:
  0.0     -1.2092   1.2092
  1.2092   0.0     -1.2092
 -1.2092   1.2092   0.0   
```
