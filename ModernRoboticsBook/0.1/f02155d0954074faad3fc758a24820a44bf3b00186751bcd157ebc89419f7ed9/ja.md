```
DistanceToSE3(mat)
```

matがSE(3)多様体からの距離を表すフロベニウスノルムを返します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> DistanceToSE3([1.0 0.0 0.0 1.2; 0.0 0.1 -0.95 1.5; 0.0 1.0 0.1 -0.9; 0.0 0.0 0.1 0.98])
0.13493053768513638
```
