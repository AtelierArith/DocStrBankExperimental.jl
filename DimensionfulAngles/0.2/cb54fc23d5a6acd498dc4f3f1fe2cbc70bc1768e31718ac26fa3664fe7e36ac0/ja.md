```
macro ua_str(unit)
```

角度次元を持つ単位を簡単に呼び出すための文字列マクロで、`DimensionfulAngles`パッケージにあります。このパッケージのすべての単位記号には`ᵃ`が付いていますが、このマクロを使用する際には接尾辞を使用するべきではありません。

内部に入るものは、有効なJulia式として解析可能である必要があります。

# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> 1.0ua"turn"
1.0 τ

julia> 1.0ua"rad" - 1.0ua"°"
0.9825467074800567 rad
```
