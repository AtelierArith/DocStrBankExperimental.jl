```
xkb_keymap_key_get_mods_for_level(keymap, key, layout, level, masks_out, masks_size)
```

指定されたシフトレベルを特定のキーとレイアウトに対して生成するすべての可能な修飾子マスクを取得します。

このAPIは逆キー変換に役立ちます。つまり、特定のキーコード、レイアウト、およびレベルに対応するキースymを入力するためにアクティブにする必要がある修飾子を見つけるために使用されます。

!!! warning
    masks_size修飾子マスクまでしか返されません。渡されたバッファが小さすぎる場合、いくつかの可能な修飾子の組み合わせは返されません。


```c++
 xkb_keymap_num_levels_for_key(keymap, key) 
```

`layout`がこのキーの範囲外（つまり、[`xkb_keymap_num_layouts_for_key`](@ref)()によって返される値以上または等しい）である場合、[`xkb_state_key_get_layout`](@ref)()と一貫した方法で範囲内に戻されます。

\since 1.0.0

### パラメータ

  * `keymap`:[in] キーマップ。
  * `key`:[in] キーのキーコード。
  * `layout`:[in] 修飾子を取得するためのレイアウト。
  * `level`:[in] 修飾子を取得するためのレイアウト内のシフトレベル。これは以下より小さい必要があります：
  * `masks_out`:[out] 要求されたマスクが格納されるバッファ。
  * `masks_size`:[out] masks_outが指すバッファ内の要素数。

### 戻り値

masks*out配列に格納された修飾子マスクの数。キーがキーマップに存在しない場合や、指定されたシフトレベルに到達できない場合は0を返し、masks*outバッファは変更されません。

### 参照

[`xkb_level_index_t`](@ref)、[`xkb_mod_mask_t`](@ref) xkb_keymap
