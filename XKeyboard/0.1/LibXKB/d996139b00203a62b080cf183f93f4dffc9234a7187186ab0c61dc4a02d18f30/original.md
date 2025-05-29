```
xkb_keymap_key_by_name(keymap, name)
```

Find the keycode of the key with the given name.

The name can be either a canonical name or an alias.

\since 0.6.0

### Returns

The keycode. If no key with this name exists, returns [`XKB_KEYCODE_INVALID`](@ref).

### See also

[`xkb_keycode_t`](@ref) xkb_keymap
