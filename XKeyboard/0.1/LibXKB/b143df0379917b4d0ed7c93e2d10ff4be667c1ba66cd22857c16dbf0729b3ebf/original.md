```
xkb_state_key_get_layout(state, key)
```

Get the effective layout index for a key in a given keyboard state.

\invariant If the returned layout is valid, the following always holds:

```c++
 xkb_state_key_get_layout(state, key) < xkb_keymap_num_layouts_for_key(keymap, key)
```

xkb_state

### Returns

The layout index for the key in the given keyboard state. If the given keycode is invalid, or if the key is not included in any layout at all, returns [`XKB_LAYOUT_INVALID`](@ref).
