```
xkb_keysym_to_utf8(keysym, buffer, size)
```

Get the Unicode/UTF-8 representation of a keysym.

This function does not perform any keysym-transformations. Therefore, prefer to use [`xkb_state_key_get_utf8`](@ref)() if possible.

### Parameters

  * `keysym`:[in] The keysym.
  * `buffer`:[out] A buffer to write the UTF-8 string into.
  * `size`:[in] The size of buffer. Must be at least 7.

### Returns

The number of bytes written to the buffer (including the terminating byte). If the keysym does not have a Unicode representation, returns 0. If the buffer is too small, returns -1.

### See also

[`xkb_state_key_get_utf8`](@ref)()
