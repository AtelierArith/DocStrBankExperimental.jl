```
xkb_keymap_get_as_string(keymap, format)
```

Get the compiled keymap as a string.

The returned string may be fed back into [`xkb_keymap_new_from_string`](@ref)() to get the exact same keymap (possibly in another process, etc.).

The returned string is dynamically allocated and should be freed by the caller.

xkb_keymap

### Parameters

  * `keymap`: The keymap to get as a string.
  * `format`: The keymap format to use for the string. You can pass in the special value [`XKB_KEYMAP_USE_ORIGINAL_FORMAT`](@ref) to use the format from which the keymap was originally created.

### Returns

The keymap as a NUL-terminated string, or NULL if unsuccessful.
