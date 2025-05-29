```
l2_range(mr::L2L1Triangle, l1::Integer)
```

イテレータによってスパンされる `l2` の範囲のサブセクションを返します。ここで `(l1,l2)` は `l1 - mr.Δl_max ⩽ l2 ⩽ l1 + mr.Δl_max` を満たします。

# 例

```jldoctest
julia> r = L2L1Triangle(1:2, 1);

julia> collect(r)
6-element Vector{Tuple{Int64, Int64}}:
 (0, 1)
 (1, 1)
 (2, 1)
 (1, 2)
 (2, 2)
 (3, 2)

julia> l2_range(r, 1)
0:2

julia> l2_range(r, 2)
1:3
```
