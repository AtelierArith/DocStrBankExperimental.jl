```
hasbangindex(x::GapObj, i::Int64)
```

位置 `i` にあるエントリが [positional object](GAP_ref(ref:IsPositionalObjectRep)) `x` に存在するかどうかを返します。

# 例

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> hasbangindex(x, 1)
true

julia> hasbangindex(x, 2)
false
```
