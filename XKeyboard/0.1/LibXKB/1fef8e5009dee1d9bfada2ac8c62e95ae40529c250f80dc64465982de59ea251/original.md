```
xkb_state_led_name_is_active(state, name)
```

Test whether a LED is active in a given keyboard state by name.

### Returns

1 if the LED is active, 0 if it not. If no LED with this name exists in the keymap, returns -1.

### See also

[`xkb_led_index_t`](@ref) xkb_state
