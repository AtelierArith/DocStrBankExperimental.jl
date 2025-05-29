```
adjustbags(b::AlignedBags, mask::AbstractVector{Bool})
```

バッグ `b` のインスタンスのインデックスを削除し、残りのインスタンスをそれに応じて再マッピングします。

# 例

```jldoctest
julia> adjustbags(AlignedBags([1:2, 0:-1, 3:4]), [false, false, true, true])
AlignedBags{Int64}(UnitRange{Int64}[0:-1, 0:-1, 1:2])
```
