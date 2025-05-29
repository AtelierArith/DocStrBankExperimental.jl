```
xkb_state_key_get_utf8(state, key, buffer, size)
```

Get the Unicode/UTF-8 string obtained from pressing a particular key in a given keyboard state.

!!! warning
    If the buffer passed is too small, the string is truncated (though still NUL-terminated).


You may check if truncation has occurred by comparing the return value with the size of `buffer`, similarly to the snprintf(3) function. You may safely pass NULL and 0 to `buffer` and `size` to find the required size (without the NUL-byte).

This function performs Capitalization and Control keysym-transformations.

xkb_state

\since 0.4.1

### Parameters

  * `state`:[in] The keyboard state object.
  * `key`:[in] The keycode of the key.
  * `buffer`:[out] A buffer to write the string into.
  * `size`:[in] Size of the buffer.

### Returns

The number of bytes required for the string, excluding the NUL byte. If there is nothing to write, returns 0.
