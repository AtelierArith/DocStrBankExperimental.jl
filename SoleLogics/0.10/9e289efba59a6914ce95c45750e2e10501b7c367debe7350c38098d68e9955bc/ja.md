```
const DIAMOND = NamedConnective{:◊}()
const ◊ = DIAMOND
ismodal(::typeof(◊)) = true
arity(::typeof(◊)) = 1
```

論理ダイヤモンド接続詞で、通常はモーダル存在量化子として解釈されます。詳細は[こちら](https://en.wikipedia.org/wiki/Modal_operator)を参照してください。

また、[`BOX`](@ref)、[`NamedConnective`](@ref)、[`Connective`](@ref)も参照してください。
