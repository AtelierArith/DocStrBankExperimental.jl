```
xkb_state_mod_index_is_active(state, idx, type)
```

Test whether a modifier is active in a given keyboard state by index.

xkb_state

### Returns

1 if the modifier is active, 0 if it is not. If the modifier index is invalid in the keymap, returns -1.
