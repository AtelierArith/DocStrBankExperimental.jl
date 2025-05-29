```
permtype(g::Perm)
```

順列 `g` のタイプを返します。すなわち、`g` のサイクル分解における互いに素なサイクルの長さです。

長さはデフォルトで降順にソートされます。`permtype(g)` は `g` の共役類を完全に決定します。

# 例

```jldoctest
julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> permtype(g)
3-element Vector{Int64}:
 3
 2
 1

julia> e = one(g)
()

julia> permtype(e)
6-element Vector{Int64}:
 1
 1
 1
 1
 1
 1
```
