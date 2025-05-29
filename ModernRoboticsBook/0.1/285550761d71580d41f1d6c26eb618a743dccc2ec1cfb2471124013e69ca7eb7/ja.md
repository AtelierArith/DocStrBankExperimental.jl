```
RpToTrans(R, p)
```

回転行列と位置ベクトルを同次変換行列に変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> RpToTrans([1 0 0; 0 0 -1; 0 1 0], [1, 2, 5])
4×4 Matrix{Int64}:
 1  0   0  1
 0  0  -1  2
 0  1   0  5
 0  0   0  1
```
