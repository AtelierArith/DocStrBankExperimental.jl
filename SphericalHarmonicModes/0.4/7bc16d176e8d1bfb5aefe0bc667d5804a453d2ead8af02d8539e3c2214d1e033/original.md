```
l2_range(mr::L2L1Triangle, l1::Integer)
```

Return a subsection of the range of `l2` spanned by the iterator for which `(l1,l2)` satisfy `l1 - mr.Δl_max ⩽ l2 ⩽ l1 + mr.Δl_max`.

# Examples

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
