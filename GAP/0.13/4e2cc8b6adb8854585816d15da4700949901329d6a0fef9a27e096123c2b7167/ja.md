```
setbangindex!(x::GapObj, v::Any, i::Int64)
```

位置 `i` にある [位置オブジェクト](GAP_ref(ref:IsPositionalObjectRep)) `x` のエントリを `v` に設定し、`x` を返します。

# 例

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> setbangindex!(x, 0, 1)
GAP: ZmodnZObj( 0, 6 )
```
