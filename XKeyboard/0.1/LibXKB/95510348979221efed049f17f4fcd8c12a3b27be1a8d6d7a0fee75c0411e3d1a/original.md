```
xkb_state_key_get_one_sym(state, key)
```

Get the single keysym obtained from pressing a particular key in a given keyboard state.

This function is similar to [`xkb_state_key_get_syms`](@ref)(), but intended for users which cannot or do not want to handle the case where multiple keysyms are returned (in which case this function is preferred).

This function performs Capitalization keysym-transformations.

### Returns

The keysym. If the key does not have exactly one keysym, returns [`XKB_KEY_NoSymbol`](@ref)

### See also

[`xkb_state_key_get_syms`](@ref)() xkb_state
