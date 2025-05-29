```
MatrixExp3(so3mat)
```

so(3)の行列の行列指数を計算します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> MatrixExp3([0 -3 2; 3 0 -1; -2 1 0])
3×3 Matrix{Float64}:
 -0.694921   0.713521  0.0892929
 -0.192007  -0.303785  0.933192 
  0.692978   0.63135   0.348107 
```
