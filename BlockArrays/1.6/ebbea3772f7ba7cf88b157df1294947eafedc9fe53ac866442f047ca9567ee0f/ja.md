```
BlockedUnitRange
```

は、ブロックに分割された `AbstractUnitRange{<:Integer}` です。構築は通常、ブロックの長さのベクトルを `BlockedUnitRange` に変換する `blockedrange` を介して行われます。

# 例

```jldoctest
julia> blockedrange(2, [2,2,3]) # 最初の値とブロックの長さ
3-blocked 7-element BlockedUnitRange{Int64, Vector{Int64}}:
 2
 3
 ─
 4
 5
 ─
 6
 7
 8
```

他にも [`BlockedOneTo`](@ref) を参照してください。
