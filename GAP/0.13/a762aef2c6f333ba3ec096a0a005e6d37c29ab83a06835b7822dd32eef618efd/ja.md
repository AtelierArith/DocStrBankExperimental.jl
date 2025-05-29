```
hasbangproperty(x::GapObj, f::Union{AbstractString,Int64,Symbol})
```

[コンポーネントオブジェクト](GAP_ref(ref:IsComponentObjectRep)）`x`がコンポーネント`f`を持っているかどうかを返します。

# 例

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> hasbangproperty(x, :counter)
true

julia> hasbangproperty(x, :x)
false
```
