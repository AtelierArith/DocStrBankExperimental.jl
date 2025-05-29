```
ItemQuantity(count::Int, noun::String)
ItemQuantity(count::Int, noun::String, noun_plural::String)
```

印刷されることだけを目的としたヘルパーオブジェクトです。`count`が`1`の場合、`1 noun`として印刷されます。それ以外の`count`の場合、出力は`count noun_plural`になります。`noun_plural`が指定されていない場合、これは`plural(noun)`にデフォルト設定されます。

明示的な複数形を指定できる理由は、[`plural`](@ref)が完璧ではなく、正しい複数形を生成しない場合があるため、フォールバックの代替手段を持つことが賢明だからです。ただし、理想的には、`pluralize`を改善してニーズに正しく対応できるようにしてください。

# 例

```jldoctest
julia> ItemQuantity(0, "generator")
0 generators

julia> ItemQuantity(1, "generator")
1 generator

julia> ItemQuantity(2, "generator")
2 generators
```

カスタム複数形の例です。

```jldoctest
julia> ItemQuantity(0, "ox", "oxen")
0 oxen

julia> ItemQuantity(1, "ox", "oxen")
1 ox

julia> ItemQuantity(2, "ox", "oxen")
2 oxen
```
