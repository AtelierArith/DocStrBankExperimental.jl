```
ScrewToAxis(q, s, h)
```

スクリュー軸のパラメトリックな記述を受け取り、正規化されたスクリュー軸に変換します。

# 例

```jldoctest; setup = :(using ModernRoboticsBook)
julia> ScrewToAxis([3; 0; 0], [0; 0; 1], 2)
6-element Vector{Int64}:
  0
  0
  1
  0
 -3
  2
```
