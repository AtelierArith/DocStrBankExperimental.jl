```
xkb_keymap_layout_get_index(keymap, name)
```

Get the index of a layout by name.

### Returns

The index. If no layout exists with this name, returns [`XKB_LAYOUT_INVALID`](@ref). If more than one layout in the keymap has this name, returns the lowest index among them.

### See also

[`xkb_layout_index_t`](@ref) For notes on layout names. xkb_keymap
