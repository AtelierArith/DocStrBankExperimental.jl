```
xkb_keymap_new_from_buffer(context, buffer, length, format, flags)
```

Create a keymap from a memory buffer.

This is just like [`xkb_keymap_new_from_string`](@ref)(), but takes a length argument so the input string does not have to be zero-terminated.

\since 0.3.0

### See also

[`xkb_keymap_new_from_string`](@ref)() xkb_keymap
