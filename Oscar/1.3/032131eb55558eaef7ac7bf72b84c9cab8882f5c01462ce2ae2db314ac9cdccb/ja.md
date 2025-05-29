```
is_empty(c::ClosedSubvarietyOfToricVariety)
```

トリック多様体の閉じた部分多様体が空であるかどうかを確認します。このチェックは、[CLS11](@cite)の命題5.2.6を使用しています。

# 例

```jldoctest
julia> f2 = hirzebruch_surface(NormalToricVariety, 2);

julia> (t1, x1, t2, x2) = gens(cox_ring(f2));

julia> c = closed_subvariety_of_toric_variety(f2, [t1])
閉じた部分多様体の正規トリック多様体

julia> is_empty(c)
false

julia> c2 = closed_subvariety_of_toric_variety(f2, [x1,x2])
閉じた部分多様体の正規トリック多様体

julia> is_empty(c2)
true
```
