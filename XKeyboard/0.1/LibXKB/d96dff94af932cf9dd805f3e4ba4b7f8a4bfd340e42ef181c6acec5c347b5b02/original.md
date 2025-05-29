```
xkb_state_key_get_consumed_mods2(state, key, mode)
```

Get the mask of modifiers consumed by translating a given key.

xkb_state

\since 0.7.0

### Parameters

  * `state`: The keyboard state.
  * `key`: The keycode of the key.
  * `mode`: The consumed modifiers mode to use; see enum description.

### Returns

a mask of the consumed modifiers.
