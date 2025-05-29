```
xkb_state_layout_index_is_active(state, idx, type)
```

Test whether a layout is active in a given keyboard state by index.

### Returns

1 if the layout is active, 0 if it is not. If the layout index is not valid in the keymap, returns -1.

### See also

[`xkb_layout_index_t`](@ref) xkb_state
