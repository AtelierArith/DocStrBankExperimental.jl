```
xkb_keymap_num_layouts_for_key(keymap, key)
```

Get the number of layouts for a specific key.

This number can be different from [`xkb_keymap_num_layouts`](@ref)(), but is always smaller. It is the appropriate value to use when iterating over the layouts of a key.

### See also

[`xkb_layout_index_t`](@ref) xkb_keymap
