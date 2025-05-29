```
xkb_keymap_key_get_syms_by_level(keymap, key, layout, level, syms_out)
```

Get the keysyms obtained from pressing a key in a given layout and shift level.

This function is like [`xkb_state_key_get_syms`](@ref)(), only the layout and shift level are not derived from the keyboard state but are instead specified explicitly.

```c++
 xkb_keymap_num_levels_for_key(keymap, key) 
```

If `layout` is out of range for this key (that is, larger or equal to the value returned by [`xkb_keymap_num_layouts_for_key`](@ref)()), it is brought back into range in a manner consistent with [`xkb_state_key_get_layout`](@ref)().

### Parameters

  * `keymap`:[in] The keymap.
  * `key`:[in] The keycode of the key.
  * `layout`:[in] The layout for which to get the keysyms.
  * `level`:[in] The shift level in the layout for which to get the keysyms. This should be smaller than:
  * `syms_out`:[out] An immutable array of keysyms corresponding to the key in the given layout and shift level.

### Returns

The number of keysyms in the syms_out array. If no keysyms are produced by the key in the given layout and shift level, returns 0 and sets syms_out to NULL.

### See also

[`xkb_state_key_get_syms`](@ref)() xkb_keymap
