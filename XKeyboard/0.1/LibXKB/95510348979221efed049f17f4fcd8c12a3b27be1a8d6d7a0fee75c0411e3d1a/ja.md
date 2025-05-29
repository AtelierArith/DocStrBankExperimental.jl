```
xkb_state_key_get_one_sym(state, key)
```

特定のキーを押したときに得られる単一のキースymを、指定されたキーボード状態から取得します。

この関数は[`xkb_state_key_get_syms`](@ref)()に似ていますが、複数のキースymが返される場合を処理できない、または処理したくないユーザー向けに意図されています（その場合、この関数が推奨されます）。

この関数は大文字変換のキースym変換を行います。

### 戻り値

キースym。キーが正確に1つのキースymを持たない場合は、[`XKB_KEY_NoSymbol`](@ref)を返します。

### 参照

[`xkb_state_key_get_syms`](@ref)() xkb_state
