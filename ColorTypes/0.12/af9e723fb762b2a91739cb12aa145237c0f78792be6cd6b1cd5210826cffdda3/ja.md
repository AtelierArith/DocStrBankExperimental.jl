```
Cbase = base_colorant_type(C::Type)
Cbase = base_colorant_type(c::Colorant)
```

指定された数値要素型なしでColorant型を返します。

例えば、次を比較します。

```
base_colorant_type(ARGB{N0f8}) === ARGB
```

対して

```
base_color_type(ARGB{N0f8})    === RGB
color_type(ARGB{N0f8})         === RGB{N0f8}
```

可能な場合、`base_colorant_type`はパラメトリックな`UnionAll`を返すので、`Cbase{T}`を使用して要素型`T`を持つ色素を指定できます。しかし、`base_colorant_type`がパラメトリックな結果を返すことは保証されていません。例えば、

```jldoctest; setup = :(using ColorTypes)
julia> base_colorant_type(RGB24)
RGB24
```

一般的なコードでは、`Cbase`が`DataType`または`UnionAll`であるかどうかを確認できます。`Cbase{T}`はそれが`UnionAll`である場合にのみ有効です。

# 使用例

色素値`c`の要素型を`Float64`に切り替える安全で簡単な方法は次のとおりです。

```
Cbase = base_colorant_type(parametric_colorant(typeof(c)))
c64 = Cbase{Float64}(c)
```
