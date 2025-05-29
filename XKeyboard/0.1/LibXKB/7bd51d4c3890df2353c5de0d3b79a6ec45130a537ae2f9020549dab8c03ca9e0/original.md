```
xkb_state_key_get_utf32(state, key)
```

Get the Unicode/UTF-32 codepoint obtained from pressing a particular key in a a given keyboard state.

This function performs Capitalization and Control keysym-transformations.

xkb_state

\since 0.4.1

### Returns

The UTF-32 representation for the key, if it consists of only a single codepoint. Otherwise, returns 0.
