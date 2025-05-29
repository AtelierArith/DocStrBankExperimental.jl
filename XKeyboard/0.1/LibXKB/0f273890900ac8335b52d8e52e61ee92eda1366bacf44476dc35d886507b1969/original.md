```
xkb_keymap_key_for_each(keymap, iter, data)
```

Run a specified function for every valid keycode in the keymap. If a keymap is sparse, this function may be called fewer than (max_keycode - min_keycode + 1) times.

\since 0.3.1

### See also

[`xkb_keymap_min_keycode`](@ref)() [`xkb_keymap_max_keycode`](@ref)() [`xkb_keycode_t`](@ref) xkb_keymap
