```
dedekind_sum(h::ZZRingElem, k::ZZRingElem)
```

Return the Dedekind sum $s(h,k)$ for arbitrary $h$ and $k$.

# Examples

```jldoctest
julia> b = dedekind_sum(12, 13)
-11//13

julia> c = dedekind_sum(-120, ZZ(1305))
-575//522
```
