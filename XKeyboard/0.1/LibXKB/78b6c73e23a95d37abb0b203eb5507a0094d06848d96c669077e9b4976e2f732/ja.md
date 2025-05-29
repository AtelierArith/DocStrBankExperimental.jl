```
xkb_state_mod_mask_remove_consumed(state, key, mask)
```

キーの修飾子マスクから消費された修飾子を削除します。

\deprecated 代わりに [`xkb_state_key_get_consumed_mods2`](@ref)() を使用してください。

指定された修飾子マスクを取り、特定のキーに対して消費されるすべての修飾子を削除します（[`xkb_state_mod_index_is_consumed`](@ref)() のように）。

### 参照

[`xkb_state_mod_index_is_consumed`](@ref)() xkb_state
