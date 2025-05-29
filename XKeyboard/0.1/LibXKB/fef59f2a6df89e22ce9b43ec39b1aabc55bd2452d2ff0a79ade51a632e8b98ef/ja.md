```
xkb_keymap_key_get_syms_by_level(keymap, key, layout, level, syms_out)
```

指定されたレイアウトとシフトレベルでキーを押すことによって得られるキーシンボルを取得します。

この関数は[`xkb_state_key_get_syms`](@ref)()に似ていますが、レイアウトとシフトレベルはキーボードの状態から導出されるのではなく、明示的に指定されます。

```c++
 xkb_keymap_num_levels_for_key(keymap, key) 
```

`layout`がこのキーの範囲外（つまり、[`xkb_keymap_num_layouts_for_key`](@ref)()によって返される値以上）である場合、それは[`xkb_state_key_get_layout`](@ref)()と一貫した方法で範囲内に戻されます。

### パラメータ

  * `keymap`:[in] キーマップ。
  * `key`:[in] キーのキーコード。
  * `layout`:[in] キーシンボルを取得するためのレイアウト。
  * `level`:[in] キーシンボルを取得するためのレイアウト内のシフトレベル。これは以下より小さい必要があります：
  * `syms_out`:[out] 指定されたレイアウトとシフトレベルに対応するキーの不変配列のキーシンボル。

### 戻り値

syms*out配列内のキーシンボルの数。指定されたレイアウトとシフトレベルでキーによって生成されるキーシンボルがない場合、0を返し、syms*outをNULLに設定します。

### 参照

[`xkb_state_key_get_syms`](@ref)() xkb_keymap
