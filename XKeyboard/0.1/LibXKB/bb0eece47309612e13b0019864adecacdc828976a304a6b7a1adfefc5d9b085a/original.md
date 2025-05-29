```
xkb_state_key_get_syms(state, key, syms_out)
```

Get the keysyms obtained from pressing a particular key in a given keyboard state.

Get the keysyms for a key according to the current active layout, modifiers and shift level for the key, as determined by a keyboard state.

As an extension to XKB, this function can return more than one keysym. If you do not want to handle this case, you can use [`xkb_state_key_get_one_sym`](@ref)() for a simpler interface.

This function does not perform any keysym-transformations. (This might change).

xkb_state

### Parameters

  * `state`:[in] The keyboard state object.
  * `key`:[in] The keycode of the key.
  * `syms_out`:[out] An immutable array of keysyms corresponding the key in the given keyboard state.

### Returns

The number of keysyms in the syms_out array. If no keysyms are produced by the key in the given keyboard state, returns 0 and sets syms_out to NULL.
