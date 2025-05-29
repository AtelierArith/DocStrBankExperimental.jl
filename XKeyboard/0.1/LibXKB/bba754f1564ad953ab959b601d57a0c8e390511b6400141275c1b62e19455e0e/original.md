```
xkb_state_led_index_is_active(state, idx)
```

Test whether a LED is active in a given keyboard state by index.

### Returns

1 if the LED is active, 0 if it not. If the LED index is not valid in the keymap, returns -1.

### See also

[`xkb_led_index_t`](@ref) xkb_state
