```
addreaction!(network::ReactionSystem, rx::Reaction)
```

渡された反応を[`ReactionSystem`](@ref)に追加します。`network`内の`Reaction`のリストにおける`rx`の整数IDを返します。

注意:

  * `rx`で使用される新しい種やパラメータは、[`addspecies!`](@ref)および[`addparam!`](@ref)を使用して別途`network`に追加する必要があります。
