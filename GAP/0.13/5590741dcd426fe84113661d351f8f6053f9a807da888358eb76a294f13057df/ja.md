```
getbangindex(x::GapObj, i::Int64)
```

位置 `i` にある [位置オブジェクト](GAP_ref(ref:IsPositionalObjectRep)) `x` のエントリを返します。

# 例

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> getbangindex(x, 1)
1
```
