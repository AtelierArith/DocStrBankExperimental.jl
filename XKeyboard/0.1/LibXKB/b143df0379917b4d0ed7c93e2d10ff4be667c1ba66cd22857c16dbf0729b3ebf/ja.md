```
xkb_state_key_get_layout(state, key)
```

指定されたキーボード状態におけるキーの有効なレイアウトインデックスを取得します。

\invariant 返されるレイアウトが有効な場合、次のことが常に成り立ちます：

```c++
 xkb_state_key_get_layout(state, key) < xkb_keymap_num_layouts_for_key(keymap, key)
```

xkb_state

### 戻り値

指定されたキーボード状態におけるキーのレイアウトインデックス。指定されたキーコードが無効であるか、キーが全くどのレイアウトにも含まれていない場合は、[`XKB_LAYOUT_INVALID`](@ref)を返します。
