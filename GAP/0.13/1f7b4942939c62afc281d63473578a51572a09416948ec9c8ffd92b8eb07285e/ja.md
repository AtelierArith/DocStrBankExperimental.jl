```
setbangproperty!(x::GapObj, f::Union{AbstractString,Int64,Symbol}, v)
```

コンポーネント `f` の値を [コンポーネントオブジェクト](GAP_ref(ref:IsComponentObjectRep)) `x` に `v` として設定し、`x` を返します。

# 例

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> setbangproperty!(x, :counter, 3)
GAP: <iterator of Integers at -1>

julia> getbangproperty(x, :counter)
3
```
