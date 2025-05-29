```
const BOX = NamedConnective{:□}()
const □ = BOX
arity(::typeof(□)) = 1
```

論理ボックス接続詞で、通常はモーダル普遍量化子として解釈されます。詳細は[こちら](https://en.wikipedia.org/wiki/Modal_operator)を参照してください。

また、[`DIAMOND`](@ref)、[`NamedConnective`](@ref)、[`Connective`](@ref)も参照してください。
