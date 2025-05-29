```
xkb_keysym_to_utf8(keysym, buffer, size)
```

キーシンのUnicode/UTF-8表現を取得します。

この関数はキーシン変換を行いません。したがって、可能であれば[`xkb_state_key_get_utf8`](@ref)()を使用することをお勧めします。

### パラメータ

  * `keysym`:[in] キーシン。
  * `buffer`:[out] UTF-8文字列を書き込むためのバッファ。
  * `size`:[in] バッファのサイズ。少なくとも7でなければなりません。

### 戻り値

バッファに書き込まれたバイト数（終端バイトを含む）。キーシンにUnicode表現がない場合は0を返します。バッファが小さすぎる場合は-1を返します。

### 参照

[`xkb_state_key_get_utf8`](@ref)()
