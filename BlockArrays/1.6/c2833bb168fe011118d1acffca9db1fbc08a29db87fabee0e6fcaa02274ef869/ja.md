```
BlockedOneTo{T, <:Union{AbstractVector{T}, NTuple{<:Any,T}}} where {T}
```

`axes` のブロック配列を表すために、ブロックに分割された `AbstractUnitRange{T}` を定義します。これは、最初の値が `1` であることが保証されている点で `Base.OneTo` に似ています。

構築は通常、ブロックの長さのベクトルを `BlockedUnitRange` に変換する `blockedrange` を介して行われます。

# 例

```jldoctest
julia> blockedrange([2,2,3]) # ブロックの長さ
3-blocked 7-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 2
 ─
 3
 4
 ─
 5
 6
 7
```

[`BlockedUnitRange`](@ref) も参照してください。
