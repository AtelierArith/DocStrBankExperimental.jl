```
getbangproperty(x::GapObj, f::Union{AbstractString,Int64,Symbol})
```

コンポーネント `f` の値を [コンポーネントオブジェクト](GAP_ref(ref:IsComponentObjectRep)) `x` から返します。

# 例

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> getbangproperty(x, :counter)
0
```
