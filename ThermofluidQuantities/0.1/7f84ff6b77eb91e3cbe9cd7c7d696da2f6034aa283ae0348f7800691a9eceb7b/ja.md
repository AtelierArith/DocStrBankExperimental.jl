```
@displayedunits 名称 単位 次元
```

量の表示に使用する単位を設定し、これらの単位を返す関数 `displayedunits` と、量をこれらの単位に変換する `ushow` を作成します。新しい単位タイプは `name` で指定され、デフォルトの単位は `unit` で、次元は `dims` で指定されます。後者は `Unitful` の次元名 `𝐌`、`𝐓`、`𝐋`、`𝚯` を組み合わせて使用します。

# 例

```jldoctest myunit
julia> import ThermofluidQuantities: 𝐋, 𝐓

julia> @displayedunits MyVelocityType "m/s" 𝐋/𝐓

julia> MyVelocityType
Union{Unitful.Quantity{T,𝐋 𝐓⁻¹,U}, Unitful.Level{L,S,Unitful.Quantity{T,𝐋 𝐓⁻¹,U}} where S where L} where U where T
```
