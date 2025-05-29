```
xkb_keymap_key_get_mods_for_level(keymap, key, layout, level, masks_out, masks_size)
```

Retrieves every possible modifier mask that produces the specified shift level for a specific key and layout.

This API is useful for inverse key transformation; i.e. finding out which modifiers need to be active in order to be able to type the keysym(s) corresponding to the specific key code, layout and level.

!!! warning
    It returns only up to masks_size modifier masks. If the buffer passed is too small, some of the possible modifier combinations will not be returned.


```c++
 xkb_keymap_num_levels_for_key(keymap, key) 
```

If `layout` is out of range for this key (that is, larger or equal to the value returned by [`xkb_keymap_num_layouts_for_key`](@ref)()), it is brought back into range in a manner consistent with [`xkb_state_key_get_layout`](@ref)().

\since 1.0.0

### Parameters

  * `keymap`:[in] The keymap.
  * `key`:[in] The keycode of the key.
  * `layout`:[in] The layout for which to get modifiers.
  * `level`:[in] The shift level in the layout for which to get the modifiers. This should be smaller than:
  * `masks_out`:[out] A buffer in which the requested masks should be stored.
  * `masks_size`:[out] The number of elements in the buffer pointed to by masks_out.

### Returns

The number of modifier masks stored in the masks_out array. If the key is not in the keymap or if the specified shift level cannot be reached it returns 0 and does not modify the masks_out buffer.

### See also

[`xkb_level_index_t`](@ref), [`xkb_mod_mask_t`](@ref) xkb_keymap
