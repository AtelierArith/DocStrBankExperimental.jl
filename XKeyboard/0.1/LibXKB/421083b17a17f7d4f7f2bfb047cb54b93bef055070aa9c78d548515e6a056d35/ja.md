```
xkb_state_mod_index_is_consumed2(state, key, idx, mode)
```

キーに対するキーボード状態の変換によって修飾子が消費されるかどうかをテストします。

\since 0.7.0

### パラメータ

  * `state`: キーボードの状態。
  * `key`: キーのキーコード。
  * `idx`: チェックする修飾子のインデックス。
  * `mode`: 使用する消費された修飾子のモード; 列挙型の説明を参照してください。

### 戻り値

修飾子が消費されている場合は1、そうでない場合は0を返します。修飾子インデックスがキーマップで有効でない場合は-1を返します。

### 参照

[`xkb_state_mod_mask_remove_consumed`](@ref)(), [`xkb_state_key_get_consumed_mods`](@ref)() xkb_state
