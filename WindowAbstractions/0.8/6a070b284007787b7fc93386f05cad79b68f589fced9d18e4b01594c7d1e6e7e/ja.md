キャラクターとキー修飾子の状態に関連付けられたキー バインディング。

```julia
struct KeyCombination
```

  * `key::WindowAbstractions.KeySymbol`
  * `exact_modifiers::WindowAbstractions.ModifierState`
  * `significant_modifiers::WindowAbstractions.ModifierState`
