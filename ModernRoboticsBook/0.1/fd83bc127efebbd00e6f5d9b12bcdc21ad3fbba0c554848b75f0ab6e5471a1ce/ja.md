```
MatrixExp6(se3mat)
```

指数座標のse3表現の行列指数を計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> MatrixExp6([0 0 0 0; 0 0 -1.57079632 2.35619449; 0 1.57079632 0 2.35619449; 0 0 0 0])
4×4 Matrix{Float64}:
 1.0  0.0         0.0        0.0       
 0.0  6.7949e-9  -1.0        1.01923e-8
 0.0  1.0         6.7949e-9  3.0       
 0.0  0.0         0.0        1.0       
```
