```
xkb_keymap_num_leds(keymap)
```

Get the number of LEDs in the keymap.

!!! warning
    The range [ 0...[`xkb_keymap_num_leds`](@ref)() ) includes all of the LEDs in the keymap, but may also contain inactive LEDs. When iterating over this range, you need the handle this case when calling functions such as [`xkb_keymap_led_get_name`](@ref)() or [`xkb_state_led_index_is_active`](@ref)().


### See also

[`xkb_led_index_t`](@ref) xkb_keymap
