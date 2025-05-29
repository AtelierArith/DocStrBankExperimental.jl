```
xkb_state_mod_index_is_consumed2(state, key, idx, mode)
```

Test whether a modifier is consumed by keyboard state translation for a key.

\since 0.7.0

### Parameters

  * `state`: The keyboard state.
  * `key`: The keycode of the key.
  * `idx`: The index of the modifier to check.
  * `mode`: The consumed modifiers mode to use; see enum description.

### Returns

1 if the modifier is consumed, 0 if it is not. If the modifier index is not valid in the keymap, returns -1.

### See also

[`xkb_state_mod_mask_remove_consumed`](@ref)(), [`xkb_state_key_get_consumed_mods`](@ref)() xkb_state
