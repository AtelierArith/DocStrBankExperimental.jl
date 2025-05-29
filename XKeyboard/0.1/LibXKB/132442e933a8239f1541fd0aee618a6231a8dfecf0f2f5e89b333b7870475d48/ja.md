```
xkb_keymap_layout_get_index(keymap, name)
```

名前によってレイアウトのインデックスを取得します。

### 戻り値

インデックス。指定された名前のレイアウトが存在しない場合は、[`XKB_LAYOUT_INVALID`](@ref)を返します。同じ名前のレイアウトがキーマップに複数存在する場合は、その中で最も低いインデックスを返します。

### 参照

[`xkb_layout_index_t`](@ref) レイアウト名に関する注意事項。 xkb_keymap
