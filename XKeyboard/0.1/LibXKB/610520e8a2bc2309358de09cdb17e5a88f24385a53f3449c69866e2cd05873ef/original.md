```
xkb_state_get_keymap(state)
```

Get the keymap which a keyboard state object is using.

This function does not take a new reference on the keymap; you must explicitly reference it yourself if you plan to use it beyond the lifetime of the state.

xkb_state

### Returns

The keymap which was passed to [`xkb_state_new`](@ref)() when creating this state object.
