```
TestIfSE3(mat)
```

matがSE(3)多様体に近いか、またはその上にある場合はtrueを返します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TestIfSE3([1.0 0.0 0.0 1.2; 0.0 0.1 -0.95 1.5; 0.0 1.0 0.1 -0.9; 0.0 0.0 0.1 0.98])
false
```
