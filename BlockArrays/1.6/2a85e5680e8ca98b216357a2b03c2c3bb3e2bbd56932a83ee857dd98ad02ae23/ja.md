```
blockedrange(blocklengths::Union{Tuple, AbstractVector})
blockedrange(first::Integer, blocklengths::Union{Tuple, AbstractVector})
```

ブロックサイズが `blocklengths` であるブロックされた `AbstractUnitRange{<:Integer}` を返します。`first` が提供されている場合、これは範囲の最初の値として使用されます。そうでない場合、ブロックの長さのみが提供されている場合、`first` は `1` と見なされます。

# 例

```jldoctest
julia> blockedrange([1,2])
2-blocked 3-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 3

julia> blockedrange(2, (1,2))
2-blocked 3-element BlockedUnitRange{Int64, Tuple{Int64, Int64}}:
 2
 ─
 3
 4
```
