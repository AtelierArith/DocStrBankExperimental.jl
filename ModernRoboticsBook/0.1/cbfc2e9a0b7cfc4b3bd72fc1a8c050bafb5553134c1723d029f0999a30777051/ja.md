```
TestIfSO3(mat)
```

matがSO(3)の多様体に近いか、またはその上にある場合はtrueを返します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TestIfSO3([1.0 0.0 0.0; 0.0 0.1 -0.95; 0.0 1.0 0.1])
false
```
