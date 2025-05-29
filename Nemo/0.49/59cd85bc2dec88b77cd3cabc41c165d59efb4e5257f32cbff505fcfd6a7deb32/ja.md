```
dedekind_sum(h::ZZRingElem, k::ZZRingElem)
```

任意の $h$ と $k$ に対するデデキンド和 $s(h,k)$ を返します。

# 例

```jldoctest
julia> b = dedekind_sum(12, 13)
-11//13

julia> c = dedekind_sum(-120, ZZ(1305))
-575//522
```
