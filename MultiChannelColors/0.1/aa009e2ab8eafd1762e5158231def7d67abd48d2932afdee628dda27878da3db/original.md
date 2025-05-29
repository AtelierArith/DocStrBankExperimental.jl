```
rgb = fluorophore_rgb"NAME"
```

Look up the RGB color associated with a fluorophore hard-coded in the string that follows. This lookup is performed at compile-time, and hence the *value* of `rgb` is visible to the compiler and may be constant-propagated.

If the fluorophore name cannot be hard-coded, use the dictionary form `fluorophore_rgb[name]`.
