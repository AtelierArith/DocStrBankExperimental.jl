```
xkb_keysym_get_name(keysym, buffer, size)
```

Get the name of a keysym.

For a description of how keysyms are named, see xkb*keysym*t.

!!! warning
    If the buffer passed is too small, the string is truncated (though still NUL-terminated); a size of at least 64 bytes is recommended.


You may check if truncation has occurred by comparing the return value with the length of buffer, similarly to the snprintf(3) function.

### Parameters

  * `keysym`:[in] The keysym.
  * `buffer`:[out] A string buffer to write the name into.
  * `size`:[in] Size of the buffer.

### Returns

The number of bytes in the name, excluding the NUL byte. If the keysym is invalid, returns -1.

### See also

[`xkb_keysym_t`](@ref)
