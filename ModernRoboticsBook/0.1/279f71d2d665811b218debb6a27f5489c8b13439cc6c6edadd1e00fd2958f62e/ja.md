```
TransToRp(T)
```

同次変換行列を回転行列と位置ベクトルに変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TransToRp([1 0 0 0; 0 0 -1 0; 0 1 0 3; 0 0 0 1])
([1 0 0; 0 0 -1; 0 1 0], [0, 0, 3])
```
