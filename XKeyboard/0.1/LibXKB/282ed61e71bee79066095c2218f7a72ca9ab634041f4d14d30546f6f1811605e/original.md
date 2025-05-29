```
xkb_state_layout_name_is_active(state, name, type)
```

Test whether a layout is active in a given keyboard state by name.

If multiple layouts in the keymap have this name, the one with the lowest index is tested.

### Returns

1 if the layout is active, 0 if it is not. If no layout with this name exists in the keymap, return -1.

### See also

[`xkb_layout_index_t`](@ref) xkb_state
