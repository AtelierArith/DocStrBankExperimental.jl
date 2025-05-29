```
@dimvar name utype
```

与えられた名前の次元変数タイプを定義し、`utype`の単位を持ちます。`utype`は、@displayedunitsマクロで作成された形式です。そのようなタイプのリストは`ThermofluidQuantities.unittypes`にあります。

# 例

```jldoctest mydimvar
julia> import ThermofluidQuantities: 𝐓

julia> @displayedunits MyTimeType "s" 𝐓

julia> @dimvar MyTimeVar MyTimeType

julia> MyTimeVar(5)
MyTimeVar = 5.0 s
```
