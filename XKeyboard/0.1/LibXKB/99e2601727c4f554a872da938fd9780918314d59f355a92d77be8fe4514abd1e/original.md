```
xkb_utf32_to_keysym(ucs)
```

Get the keysym corresponding to a Unicode/UTF-32 codepoint.

This function is the inverse of xkb*keysym*to_utf32. In cases where a single codepoint corresponds to multiple keysyms, returns the keysym with the lowest value.

Unicode codepoints which do not have a special (legacy) keysym encoding use a direct encoding scheme. These keysyms don't usually have an associated keysym constant (XKB_KEY_*).

For noncharacter Unicode codepoints and codepoints outside of the defined Unicode planes this function returns [`XKB_KEY_NoSymbol`](@ref).

\since 1.0.0

### Returns

The keysym corresponding to the specified Unicode codepoint, or [`XKB_KEY_NoSymbol`](@ref) if there is none.

### See also

[`xkb_keysym_to_utf32`](@ref)()
