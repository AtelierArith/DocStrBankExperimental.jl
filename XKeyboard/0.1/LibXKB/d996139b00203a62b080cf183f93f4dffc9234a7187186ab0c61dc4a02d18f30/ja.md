```
xkb_keymap_key_by_name(keymap, name)
```

指定された名前のキーのキーコードを取得します。

名前は、標準名またはエイリアスのいずれかである可能性があります。

\since 0.6.0

### 戻り値

キーコード。この名前のキーが存在しない場合は、[`XKB_KEYCODE_INVALID`](@ref)を返します。

### 参照

[`xkb_keycode_t`](@ref) xkb_keymap
