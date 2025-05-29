```
xkb_keymap_num_levels_for_key(keymap, key, layout)
```

Get the number of shift levels for a specific key and layout.

If `layout` is out of range for this key (that is, larger or equal to the value returned by [`xkb_keymap_num_layouts_for_key`](@ref)()), it is brought back into range in a manner consistent with [`xkb_state_key_get_layout`](@ref)().

### See also

[`xkb_level_index_t`](@ref) xkb_keymap
