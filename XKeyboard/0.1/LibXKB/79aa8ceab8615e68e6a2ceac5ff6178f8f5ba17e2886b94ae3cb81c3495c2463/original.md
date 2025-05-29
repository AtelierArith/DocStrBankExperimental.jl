```
xkb_keymap_new_from_names(context, names, flags)
```

Create a keymap from RMLVO names.

The primary keymap entry point: creates a new XKB keymap from a set of RMLVO (Rules + Model + Layouts + Variants + Options) names.

### Parameters

  * `context`: The context in which to create the keymap.
  * `names`: The RMLVO names to use. See [`xkb_rule_names`](@ref).
  * `flags`: Optional flags for the keymap, or 0.

### Returns

A keymap compiled according to the RMLVO names, or NULL if the compilation failed.

### See also

[`xkb_rule_names`](@ref) xkb_keymap
