```
blockfirsts(a::AbstractUnitRange{<:Integer})
```

各ブロックの最初のインデックスを返します。

# 例

```jldoctest
julia> b = blockedrange([1,2,3])
3-blocked 6-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 3
 ─
 4
 5
 6

julia> blockfirsts(b)
3-element Vector{Int64}:
 1
 2
 4
```
