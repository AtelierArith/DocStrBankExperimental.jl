```
xkb_state_key_get_level(state, key, layout)
```

Get the effective shift level for a key in a given keyboard state and layout.

```c++
 xkb_keymap_num_layouts_for_key(keymap, key) 
```

usually it would be:

```c++
 xkb_state_key_get_layout(state, key) 
```

\invariant If the returned level is valid, the following always holds:

```c++
 xkb_state_key_get_level(state, key, layout) < xkb_keymap_num_levels_for_key(keymap, key, layout)
```

xkb_state

### Parameters

  * `state`: The keyboard state.
  * `key`: The keycode of the key.
  * `layout`: The layout for which to get the shift level. This must be smaller than:

### Returns

The shift level index. If the key or layout are invalid, returns [`XKB_LEVEL_INVALID`](@ref).
