```
xkb_state_key_get_level(state, key, layout)
```

指定されたキーボード状態とレイアウトにおけるキーの有効なシフトレベルを取得します。

```c++
 xkb_keymap_num_layouts_for_key(keymap, key) 
```

通常は次のようになります：

```c++
 xkb_state_key_get_layout(state, key) 
```

\invariant 返されたレベルが有効である場合、次のことが常に成り立ちます：

```c++
 xkb_state_key_get_level(state, key, layout) < xkb_keymap_num_levels_for_key(keymap, key, layout)
```

xkb_state

### パラメータ

  * `state`: キーボードの状態。
  * `key`: キーのキーコード。
  * `layout`: シフトレベルを取得するためのレイアウト。これは次の値より小さくなければなりません：

### 戻り値

シフトレベルのインデックス。キーまたはレイアウトが無効な場合、[`XKB_LEVEL_INVALID`](@ref)を返します。
