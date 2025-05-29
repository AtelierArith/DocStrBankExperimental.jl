```
xkb_keymap_mod_get_index(keymap, name)
```

名前による修飾子のインデックスを取得します。

### 戻り値

インデックス。指定された名前の修飾子が存在しない場合は、[`XKB_MOD_INVALID`](@ref)を返します。

### 参照

[`xkb_mod_index_t`](@ref) xkb_keymap
