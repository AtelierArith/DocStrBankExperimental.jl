```
xkb_keymap_num_layouts_for_key(keymap, key)
```

特定のキーのレイアウト数を取得します。

この数は[`xkb_keymap_num_layouts`](@ref)()とは異なる場合がありますが、常に小さいです。キーのレイアウトを反復処理する際に使用する適切な値です。

### 参照

[`xkb_layout_index_t`](@ref) xkb_keymap
