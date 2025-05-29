```
xkb_keymap_key_for_each(keymap, iter, data)
```

キーマップ内のすべての有効なキーコードに対して指定された関数を実行します。キーマップがスパースである場合、この関数は (max*keycode - min*keycode + 1) 回未満呼び出されることがあります。

\since 0.3.1

### 参照

[`xkb_keymap_min_keycode`](@ref)() [`xkb_keymap_max_keycode`](@ref)() [`xkb_keycode_t`](@ref) xkb_keymap
