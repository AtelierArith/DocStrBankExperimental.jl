```
xkb_keymap_num_levels_for_key(keymap, key, layout)
```

特定のキーとレイアウトのシフトレベルの数を取得します。

`layout`がこのキーの範囲外（つまり、[`xkb_keymap_num_layouts_for_key`](@ref)()によって返される値以上）である場合、それは[`xkb_state_key_get_layout`](@ref)()と一貫した方法で範囲内に戻されます。

### 参照

[`xkb_level_index_t`](@ref) xkb_keymap
