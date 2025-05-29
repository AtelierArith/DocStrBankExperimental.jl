```
xkb_keymap_key_get_name(keymap, key)
```

Find the name of the key with the given keycode.

This function always returns the canonical name of the key (see description in [`xkb_keycode_t`](@ref)).

\since 0.6.0

### Returns

The key name. If no key with this keycode exists, returns NULL.

### See also

[`xkb_keycode_t`](@ref) xkb_keymap
