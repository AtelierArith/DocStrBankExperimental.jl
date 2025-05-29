```
xkb_keymap_new_from_buffer(context, buffer, length, format, flags)
```

メモリバッファからキーマップを作成します。

これは [`xkb_keymap_new_from_string`](@ref)() と同様ですが、入力文字列がゼロ終端である必要がないように長さ引数を取ります。

\since 0.3.0

### 参照

[`xkb_keymap_new_from_string`](@ref)() xkb_keymap
