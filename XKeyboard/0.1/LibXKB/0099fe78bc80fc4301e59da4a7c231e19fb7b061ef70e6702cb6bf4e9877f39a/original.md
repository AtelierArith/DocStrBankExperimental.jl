```
xkb_keysym_to_utf32(keysym)
```

Get the Unicode/UTF-32 representation of a keysym.

This function does not perform any keysym-transformations. Therefore, prefer to use [`xkb_state_key_get_utf32`](@ref)() if possible.

### Returns

The Unicode/UTF-32 representation of keysym, which is also compatible with UCS-4. If the keysym does not have a Unicode representation, returns 0.

### See also

[`xkb_state_key_get_utf32`](@ref)()
