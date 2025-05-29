```
blocklengths(a::AbstractUnitRange{<:Integer})
```

`a`の各ブロックの長さを返します。

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

julia> blocklengths(b)
3-element Vector{Int64}:
 1
 2
 3
```
