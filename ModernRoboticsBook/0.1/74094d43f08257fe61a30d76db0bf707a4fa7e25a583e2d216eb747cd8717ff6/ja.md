```
NearZero(z)
```

スカラーがゼロとして扱うのに十分小さいかどうかを判断します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> NearZero(-1e-7)
true
```
