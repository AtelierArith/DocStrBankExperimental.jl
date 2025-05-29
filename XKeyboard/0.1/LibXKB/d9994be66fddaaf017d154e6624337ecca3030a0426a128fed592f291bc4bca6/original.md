```
xkb_keysym_from_name(name, flags)
```

Get a keysym from its name.

If you use the XKB_KEYSYM_CASE_INSENSITIVE flag and two keysym names differ only by case, then the lower-case keysym is returned. For instance, for KEY_a and KEY_A, this function would return KEY_a for the case-insensitive search. If this functionality is needed, it is recommended to first call this function without this flag; and if that fails, only then to try with this flag, while possibly warning the user he had misspelled the name, and might get wrong results.

Case folding is done according to the C locale; the current locale is not consulted.

### Parameters

  * `name`: The name of a keysym. See remarks in [`xkb_keysym_get_name`](@ref)(); this function will accept any name returned by that function.
  * `flags`: A set of flags controlling how the search is done. If invalid flags are passed, this will fail with [`XKB_KEY_NoSymbol`](@ref).

### Returns

The keysym. If the name is invalid, returns [`XKB_KEY_NoSymbol`](@ref).

### See also

[`xkb_keysym_t`](@ref)
