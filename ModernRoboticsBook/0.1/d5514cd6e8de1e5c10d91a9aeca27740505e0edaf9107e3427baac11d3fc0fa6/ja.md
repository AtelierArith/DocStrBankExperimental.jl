```
DistanceToSO3(mat)
```

matがSO(3)多様体からの距離を記述するフロベニウスノルムを返します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> DistanceToSO3([1.0 0.0 0.0; 0.0 0.1 -0.95; 0.0 1.0 0.1])
0.08835298523536149
```
