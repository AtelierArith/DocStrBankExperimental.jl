```
xkb_keymap_key_get_name(keymap, key)
```

指定されたキーコードのキーの名前を取得します。

この関数は常にキーの標準名を返します（[`xkb_keycode_t`](@ref)の説明を参照）。

\since 0.6.0

### 戻り値

キー名。指定されたキーコードのキーが存在しない場合は、NULLを返します。

### 参照

[`xkb_keycode_t`](@ref) xkb_keymap
