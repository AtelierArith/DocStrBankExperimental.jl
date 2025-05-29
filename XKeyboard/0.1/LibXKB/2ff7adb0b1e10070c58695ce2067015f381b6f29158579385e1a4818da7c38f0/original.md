```
xkb_state_mod_name_is_active(state, name, type)
```

Test whether a modifier is active in a given keyboard state by name.

xkb_state

### Returns

1 if the modifier is active, 0 if it is not. If the modifier name does not exist in the keymap, returns -1.
