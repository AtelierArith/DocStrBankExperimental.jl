```
xkb_keysym_to_utf32(keysym)
```

キーシンのUnicode/UTF-32表現を取得します。

この関数はキーシン変換を行いません。したがって、可能であれば[`xkb_state_key_get_utf32`](@ref)()を使用することをお勧めします。

### 戻り値

キーシンのUnicode/UTF-32表現で、UCS-4とも互換性があります。キーシンにUnicode表現がない場合は、0を返します。

### 参照

[`xkb_state_key_get_utf32`](@ref)()
